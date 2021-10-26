# registry-docker-compose
Simple docker-composes for creating a private docker registry with and without authentication

To create htpasswd file you need to use `htpasswd`.

To install on Ubuntu/Debian:
```
sudo apt install apache2-utils -y
```

Create a new user:
```
htpasswd -B -n admin
```

Then insert the new encrypted password in the file

### Docker registry with Minio
You can also use s3 object storage as the private registry data store. In here we use [Minio](https://min.io/) which is a High Performance Object Storage released under GNU Public License v3.0 and also it is APIcompatible with Amazon S3 cloud storage service.

To deploy `cd` to `docker-registry-minio` directory and up the services.
#### Note: The default minio credentilas are `minioadmin` which can be found in docker logs.
If you want to create an access-key and secret-key define the following in docker-compose environment section for minio:
```
minio:

  ...

  environment:
     MINIO_ROOT_USER=master-user
     MINIO_ROOT_PASSWORD=master-password
```
