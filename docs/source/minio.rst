MinIO
=====

Instructions how to configure MinIO and Elastic Stack for creating snapshots.

Create IAM Policy
-----------------

Create a policy named "``myorg-es-readwrite``":

.. code-block:: json

    {
        "Version": "2012-10-17",
        "Statement": [
            {
                "Effect": "Allow",
                "Action": [
                    "s3:ListBucket",
                    "s3:GetBucketLocation",
                    "s3:ListBucketMultipartUploads",
                    "s3:ListBucketVersions"
                ],
                "Resource": "arn:aws:s3:::myorg-es"
            },
            {
                "Effect": "Allow",
                "Action": [
                    "s3:GetObject",
                    "s3:PutObject",
                    "s3:DeleteObject",
                    "s3:AbortMultipartUpload",
                    "s3:ListMultipartUploadParts"
                ],
                "Resource": "arn:aws:s3:::myorg-es/*"
            }
        ]
    }

Create MinIO User for Managing Elasticsearch Service Account
------------------------------------------------------------

Create a new user with the following options:

* Access Key: ``myorg-es-admin``
* Secret Key: ``abcde12345``
* Assign Policies: ``myorg-es-readwrite``

.. warning::

    User ``myorg-es-admin`` will be strictly used for login MinIO console and manage service accounts. DO NOT use it on Elasticsearch or any services. Instead, use it's service account.

Create MinIO Service Account for Elasticsearch
----------------------------------------------

Logout from root account and re-login as ``myorg-es-admin``. Then, create a new service account for the user ``myorg-es-admin``:

* Customize Credentials: ``OFF``
* Restrict with policy: ``OFF``

.. note::

    Make sure to remember the service account access key and secret key. These keys will be used on Elasticsearch masters and data instances.

Create Elasticsearch Bucket
---------------------------

Create Elasticsearch bucket named ``myorg-es``.

Create Snapshots
----------------

Go to https://KIBANA_SERVER_IP:5601/app/management/data/snapshot_restore/snapshots and ``Register a repository``.

* Repository name: minio-repo
* Repository type: AWS S3
* Client: default
* Bucket: myorg-es
* Basepath:
* Chunksize:
* Server-side encryption: no
* Buffer size:
* Canned ACL: private
* Storage class: standard
* Max snapshot bytes per second:
* Max restore bytes per second:
* Read-only: no
