FROM ubuntu:22.04

RUN apt update && apt install -y \
    curl \
    dnsutils \
    iputils-ping \
    net-tools \
    ca-certificates \
    --no-install-recommends && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /app

RUN mkdir -p /app/odoh-client-build

CMD ["/bin/bash"]