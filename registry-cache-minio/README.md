# Docker Registry and Cache with Minio

### Services
* minio

Minio is used as the `S3` datastore for storing docker images. You need to provide the following variables in `.env` file before running Minio:
```
MINIO_ACCESS_KEY
MINIO_SECRET_KEY
```
After Minio is up successfully, create a bucket with Minio UI on port 9001 or using [Minio Client](https://docs.min.io/docs/minio-client-quickstart-guide.html).
### Note: Use `MINIO_ACCESS_KEY` and `MINIO_SECRET_KEY` values to log in to the web console


Then provide the below variables and run the other services.
```
MINIO_BUCKET
MINIO_REGION_ENDPOINT
DOCKER_PROXY_USERNAME
DOCKER_PROXY_PASSWORD
```
* cache

Cache is only for pulling the images. You cannot directly push to cache service on port 5001. 
```
#Pull
docker pull serverip:5001/library/nginx:latest
```
* registry

Registry is for pulling/pushing the images. You cannot directly pull/push from/to registry on port 5000. 
```
# Push
docker push serverip:5000/nginx:1.16
# Pull
docker pull serverip:5000/nginx:1.16
```
### Note: You need to login before push/pull an image. If you want to disable authentication just comment out the volume in cache/registry service:
```
   ...
    volumes:
         - ./files/passwd:/auth/passwd:ro
```
### and also remove the following from config.yml files for cache and registry before building the images:
```
...
    auth:
    htpasswd:
        realm: basic-realm
        path: /auth/passwd
```

The default username and password for cache and registry:
```
user: admin
password: 1234
```

If you want to update the user and password use `htpasswd`:
```
sudo apt install apache2-utils -y

htpasswd -B -n user_name
```
Then insert the new encrypted password in the passwd:
```
files/passwd
```
