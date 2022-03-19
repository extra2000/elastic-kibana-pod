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

Creating Keystore
~~~~~~~~~~~~~~~~~

Create ``kibana-config`` volume and then create keystore into the volume:

.. code-block:: bash

    podman volume create kibana-config
    podman run -it --rm -v kibana-config:/usr/share/kibana/config:rw --entrypoint=bash localhost/extra2000/elastic/kibana
    ./bin/kibana-keystore create
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.encryptedSavedObjects.encryptionKey
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.security.encryptionKey
    openssl rand -hex 32 | ./bin/kibana-keystore add xpack.reporting.encryptionKey

.. note::

    The ``openssl rand -hex 32`` is a trick to generate random string.

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
