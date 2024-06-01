ARG ALPINE_VERSION=3.20

FROM golang:1.22-alpine${ALPINE_VERSION} AS builder

FROM builder AS svu

RUN go install github.com/caarlos0/svu@latest

FROM alpine:${ALPINE_VERSION} AS runtime

RUN apk add --no-cache git

COPY --from=svu /go/bin/svu /usr/local/bin/svu


