FROM node:22-alpine3.18

RUN apk add --no-cache \
    bash \
    ca-certificates

RUN npm install -g vercel@latest

ENTRYPOINT ["bash"]
