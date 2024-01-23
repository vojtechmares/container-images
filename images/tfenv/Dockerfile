FROM debian:bookworm-slim

RUN apt-get update \
  && apt-get install -y \
  ca-certificates \
  git \
  unzip \
  curl \
  && rm -rf /var/cache/apt/archives

RUN git clone --depth=1 https://github.com/tfutils/tfenv.git /opt/tfenv \
  && ln -s /opt/tfenv/bin/* /usr/local/bin \
  && mkdir -m 777 /opt/tfenv/versions
