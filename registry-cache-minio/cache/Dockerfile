FROM registry:2

ARG MINIO_ACCESS_KEY
ARG MINIO_SECRET_KEY
ARG MINIO_BUCKET
ARG MINIO_REGION_ENDPOINT
ARG DOCKER_PROXY_USERNAME
ARG DOCKER_PROXY_PASSWORD

copy config.yml /etc/docker/registry/config.yml


RUN set -ex \
    && sed -i "s|MINIO_ACCESS_KEY|$MINIO_ACCESS_KEY|g" /etc/docker/registry/config.yml \ 
    && sed -i "s|MINIO_SECRET_KEY|$MINIO_SECRET_KEY|g" /etc/docker/registry/config.yml \ 
    && sed -i "s|MINIO_BUCKET|$MINIO_BUCKET|g" /etc/docker/registry/config.yml \ 
    && sed -i "s|MINIO_REGION_ENDPOINT|$MINIO_REGION_ENDPOINT|g" /etc/docker/registry/config.yml \ 
    && sed -i "s|DOCKER_PROXY_USERNAME|$DOCKER_PROXY_USERNAME|g" /etc/docker/registry/config.yml \ 
    && sed -i "s|DOCKER_PROXY_PASSWORD|$DOCKER_PROXY_PASSWORD|g" /etc/docker/registry/config.yml
 
