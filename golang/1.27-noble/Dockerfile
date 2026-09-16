FROM --platform=linux/amd64 curlimages/curl:8.22.0 AS download-golang

WORKDIR /tmp

RUN curl -LO --fail https://go.dev/dl/go1.27.1.linux-amd64.tar.gz

FROM ubuntu:24.04

RUN apt-get update \
    && apt-get install -y --no-install-recommends ca-certificates \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /tmp

COPY --from=download-golang /tmp/go1.27.1.linux-amd64.tar.gz go1.27.1.linux-amd64.tar.gz

RUN tar -C /usr/local -xzf go1.27.1.linux-amd64.tar.gz \
    && rm go1.27.1.linux-amd64.tar.gz

ENV PATH=$PATH:/usr/local/go/bin
ENV GOPATH=/root/go
ENV PATH="${GOPATH}/bin:${PATH}"

WORKDIR /

