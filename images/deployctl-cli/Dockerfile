FROM denoland/deno:alpine

RUN apk add --no-cache \
    bash \
    ca-certificates

RUN deno install -A --no-check -r -f https://deno.land/x/deploy/deployctl.ts

ENTRYPOINT ["bash"]
