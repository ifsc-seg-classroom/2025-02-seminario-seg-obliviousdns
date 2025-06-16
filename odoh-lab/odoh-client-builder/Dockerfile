FROM golang:1.22-bookworm

RUN apt update && apt install -y git --no-install-recommends && rm -rf /var/lib/apt/lists/*

WORKDIR /app/odoh-client
RUN git clone https://github.com/cloudflare/odoh-client-go.git .

WORKDIR /app/output