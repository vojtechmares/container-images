FROM debian:bookworm-slim

USER root

RUN apt-get update \
  && apt-get install -y \
  ca-certificates \
  git \
  && rm -rf /var/cache/apt/archives/*

RUN git clone --depth=1 https://github.com/tfutils/tfenv.git ~/.tfenv
RUN echo 'export PATH="$HOME/.tfenv/bin:$PATH"' >> ~/.bashrc
