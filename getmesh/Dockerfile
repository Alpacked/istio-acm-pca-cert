FROM alpine:3.13.6

ENV GETMESH_VERSION 1.1.3

RUN apk add --update --no-cache wget curl

RUN wget https://github.com/tetratelabs/getmesh/releases/download/v${GETMESH_VERSION}/getmesh_${GETMESH_VERSION}_linux_amd64.tar.gz -O - | tar -xz \
    && curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" \
    && mv getmesh kubectl /usr/bin \
    && chmod +x /usr/bin/getmesh /usr/bin/kubectl \
    && getmesh fetch

WORKDIR /app