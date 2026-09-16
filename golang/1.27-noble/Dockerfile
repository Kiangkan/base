FROM --platform=linux/amd64 curlimages/curl:8.22.0 AS download-golang

WORKDIR /tmp

RUN curl -LO --fail https://go.dev/dl/go1.27.1.linux-amd64.tar.gz

FROM ubuntu:24.04

WORKDIR /tmp

COPY --from=download-golang /tmp/go1.27.1.linux-amd64.tar.gz go1.27.1.linux-amd64.tar.gz

RUN tar -C /usr/local -xzf go1.27.1.linux-amd64.tar.gz \
    && rm go1.27.1.linux-amd64.tar.gz

ENV PATH=$PATH:/usr/local/go/bin
ENV PATH="$PATH:$(go env GOPATH)/bin"

WORKDIR /

