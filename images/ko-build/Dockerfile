FROM alpine:3.20 AS ko

COPY --from=golang:1.23-alpine3.19 /usr/local/go /usr/local/go
ENV PATH=$PATH:/usr/local/go/bin

RUN echo https://dl-cdn.alpinelinux.org/alpine/edge/testing/ >> /etc/apk/repositories
RUN apk add --no-cache ko docker-cli

CMD ["/bin/sh"]
