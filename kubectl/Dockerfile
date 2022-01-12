FROM alpine AS builder

ARG HELM_VERSION="v3.7.2"
RUN apk add --no-cache curl
RUN wget -q https://get.helm.sh/helm-${HELM_VERSION}-linux-amd64.tar.gz -O - \
    | tar -xzO linux-amd64/helm > /bin/helm && \
    chmod +x /bin/helm
RUN curl -sfL "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl" -o /bin/kubectl

FROM scratch
COPY --from=builder /bin/helm /helm
COPY --from=builder /bin/kubectl /kubectl
