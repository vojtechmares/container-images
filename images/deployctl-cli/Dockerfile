FROM denoland/deno:alpine

RUN apk add --no-cache \
    bash \
    ca-certificates

RUN deno install --global -Arf jsr:@deno/deployctl

ENTRYPOINT ["bash"]
