FROM debian:bullseye-slim

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        mount \
        nfs-common \
        netbase \
    && rm -rf /var/lib/apt/lists/*
