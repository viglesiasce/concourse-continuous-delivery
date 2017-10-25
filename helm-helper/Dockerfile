FROM google/cloud-sdk

ENV HELM_VERSION=2.6.0

RUN apt-get update && apt-get install -y git
RUN curl -O https://storage.googleapis.com/kubernetes-helm/helm-v${HELM_VERSION}-linux-amd64.tar.gz && \
    tar zxfv helm-v${HELM_VERSION}-linux-amd64.tar.gz && \
    cp linux-amd64/helm /usr/local/bin
RUN helm init --client-only
RUN helm plugin install https://github.com/viglesiasce/helm-gcs.git