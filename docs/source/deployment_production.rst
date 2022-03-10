Deployment for General Purpose
==============================

Example how to deploy a Kibana instance for general purpose using Podman.

Getting Started
---------------

Clone repository and then ``cd`` into the project's root:

.. code-block:: bash

    mkdir ~/extra2000
    cd ~/extra2000
    git clone https://github.com/extra2000/elastic-kibana-pod.git
    cd elastic-kibana-pod

From the project's root directory, ``cd`` into ``deployment/production/kibana/``:

.. code-block:: bash

    cd deployment/production/kibana/

Build our Kibana image:

.. code-block:: bash

    podman build -t extra2000/elastic/kibana -f Dockerfile.amd64 .

Get CA from ``elastic-elasticsearch-pod`` Project
-------------------------------------------------

From the project's root directory, ``cd`` into ``deployment/production/kibana/``:

.. code-block:: bash

    cd deployment/production/kibana/

Then, get CA certificate from ``_global_secrets_`` and ``es-coord-01`` instance:

.. code-block:: bash

    cp -v /path/to/elastic-elasticsearch-pod/deployment/_global_secrets_/elastic-ca.p12 ./secrets/
    cp -v /path/to/elastic-elasticsearch-pod/deployment/examples/cluster-multi-servers/es-coord-01/secrets/elasticsearch-ssl-http/kibana/elasticsearch-ca.pem ./secrets/elastic-ca.pem

.. note::

    The ``elastic-ca.p12`` file is only used for signing certificates and should not be distributed.

Prerequisites for ``kibana``
----------------------------

From the project's root directory, ``cd`` into ``deployment/production/kibana/``:

.. code-block:: bash

    cd deployment/production/kibana/

Create Config Files
~~~~~~~~~~~~~~~~~~~

.. code-block:: bash

    cp -v configmaps/kibana.yaml{.example,}
    cp -v configs/kibana.yml{.example,}

Create pod file:

.. code-block:: bash

    cp -v kibana-pod.yaml{.example,}

Creating HTTP Certificate
~~~~~~~~~~~~~~~~~~~~~~~~~

Ensure the ``./secrets`` and ``./configs`` directories are labeled as ``container_file_t``:

.. code-block:: bash

    chcon -R -v -t container_file_t ./secrets ./configs

Create HTTP certificate:

.. code-block:: bash

    podman run -it --network none --rm -v ./secrets:/tmp/secrets:rw localhost/extra2000/elastic/elasticsearch ./bin/elasticsearch-certutil cert --ca /tmp/secrets/elastic-ca.p12 --multiple

.. list-table:: Questions and answers for creating ``kibana``'s ``certificate-bundle.zip``
   :widths: 50 50
   :header-rows: 1

   * - Question
     - Answer
   * - Enter password for CA (``/tmp/secrets/elastic-ca.p12``)
     - ``abcde12345``
   * - Enter instance name
     - ``kibana``
   * - Enter name for directories and files of ``kibana``
     - ``kibana``
   * - Enter IP Addresses for instance
     - ``SERVER_IP``,``127.0.0.1``
   * - Enter DNS names for instance
     - ``SERVER_FQDN``, ``localhost``
   * - Would you like to specify another instance?
     - ``n``
   * - Please enter the desired output file
     - ``/tmp/secrets/certificate-bundle.zip``
   * - Enter password for ``kibana/kibana.p12``
     - ``abcde12345``

Extract the certificate archive:

.. code-block:: bash

    unzip ./secrets/certificate-bundle.zip -d ./secrets/certificate-bundle

Verify the ``kibana.p12`` certificate:

.. code-block:: bash

    openssl pkcs12 -in ./secrets/certificate-bundle/kibana/kibana.p12 -nodes | openssl x509 -noout -text | less

Creating Keystore
~~~~~~~~~~~~~~~~~

Create ``./secrets/kibana-pod.keystore`` file to store certificate passwords:

.. code-block:: bash

    podman run -it --rm -v ./secrets:/tmp/secrets:rw --user root --entrypoint bash localhost/extra2000/elastic/kibana
    ./bin/kibana-keystore create
    ./bin/kibana-keystore add server.ssl.keystore.password
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.encryptedSavedObjects.encryptionKey
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.security.encryptionKey
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.reporting.encryptionKey
    cp -v /usr/share/kibana/config/kibana.keystore /tmp/secrets/kibana.keystore

.. note::

    The ``openssl rand -hex 32`` is a trick to generate random string.

Distribute Secrets
~~~~~~~~~~~~~~~~~~

Copy the created certificates and keystore to the node:

.. code-block:: bash

    scp -r -P 22 secrets/certificate-bundle secrets/kibana.keystore secrets/elastic-ca.pem USER@kibana:extra2000/elastic-kibana-pod/deployment/production/kibana/secrets/

On the node, don't forget to label the ``secrets`` directory as ``container_file_t``:

.. code-block:: bash

    chcon -R -v -t container_file_t ./secrets

Load SELinux Security Policy
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Create SELinux Security Policy:

.. code-block:: bash

    cp -v selinux/kibana_podman.cil{.example,}

Load the security policy:

.. code-block:: bash

    sudo semodule -i selinux/kibana_podman.cil /usr/share/udica/templates/{base_container.cil,net_container.cil}

Verify that the SELinux module exists:

.. code-block:: bash

    sudo semodule --list | grep -e "kibana_podman"

Deployment
----------

Import ``./secrets/elastic-ca.pem`` into your web-browser certificate authority.

.. note::

    On your web-browser, the certificate name ``./secrets/elastic-ca.pem`` will be known as "Elastic Certificate Tool Autogenerated CA".

Deploy ``kibana``
~~~~~~~~~~~~~~~~~

.. code-block:: bash

    podman play kube --configmap configmaps/kibana.yaml --seccomp-profile-root ./seccomp kibana-pod.yaml

Kibana is now accessible at https://KIBANA_SERVER_IP:5601. Login with username ``elastic`` and password ``abcde12345``.

Generate ``systemd`` files and enable on ``boot``:

.. code-block:: bash

    mkdir -pv ~/.config/systemd/user
    cd ~/.config/systemd/user
    podman generate systemd --files --name kibana-pod
    systemctl --user enable pod-kibana-pod.service container-kibana-pod-srv01.service
