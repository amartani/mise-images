ARG BASE_IMAGE
ARG MISE_VERSION

FROM ${BASE_IMAGE}
ARG MISE_VERSION
RUN savedAptMark="$(apt-mark showmanual)" && \
    apt-get update && apt-get install -y curl ca-certificates && \
    mkdir -p /etc/apt/keyrings && \
    curl -fSs https://mise.en.dev/gpg-key.pub | tee /etc/apt/keyrings/mise-archive-keyring.asc && \
    echo "deb [signed-by=/etc/apt/keyrings/mise-archive-keyring.asc] https://mise.en.dev/deb stable main" > /etc/apt/sources.list.d/mise.list && \
    apt-get update && apt-get install -y mise=${MISE_VERSION} && \
    apt-mark manual $savedAptMark mise && \
    apt-get purge -y --auto-remove -o APT::AutoRemove::RecommendsImportant=false && \
    rm -rf /var/lib/apt/lists/* && \
    mise --version
