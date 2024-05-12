FROM alpine:3.19

RUN echo https://dl-cdn.alpinelinux.org/alpine/edge/testing/ >> /etc/apk/repositories
RUN apk add --no-cache ko docker-cli

CMD ["/bin/sh"]
