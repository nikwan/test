# test
test
FROM alpine

# Ignore to update versions here
# docker build --no-cache --build-arg KUBECTL_VERSION=${tag} --build-arg HELM_VERSION=${helm} --build-arg KUSTOMIZE_VERSION=${kustomize_version} -t ${image}:${tag} .
ARG HELM_VERSION=3.2.1
ARG KUBECTL_VERSION=1.26.1
ARG KUSTOMIZE_VERSION=v3.8.1
ARG KUBESEAL_VERSION=0.18.1

#https://dl.k8s.io/release/v1.26.0/bin/linux/amd64/kubectl

RUN apk add --update --no-cache curl

# Install kubectl 
RUN curl -sLO https://dl.k8s.io/release/v${KUBECTL_VERSION}/bin/linux/amd64/kubectl && \
    mv kubectl /usr/bin/kubectl && \
    chmod +x /usr/bin/kubectl


WORKDIR /apps
