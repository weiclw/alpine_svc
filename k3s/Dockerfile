# Please build "alpine_svc" docker image first.
# Please use "--privileged" flag to start the built image.
from alpine_svc:latest

RUN curl -sfL https://get.k3s.io | sh - || true &&\
    export VERIFY_CHECKSUM=false &&\
    curl -fsSL https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | sh -

# So that the containerd can mount an overlayfs inside;
# Note: This means that the container shall be started with --privileged flag.
VOLUME [ "/var/lib/rancher" ]

# For tools such as helm to connect to k3s.
ENV KUBECONFIG=/etc/rancher/k3s/k3s.yaml