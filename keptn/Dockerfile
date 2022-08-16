FROM ubuntu AS builder

ARG KEPTN_VERSION="0.16.1"

RUN apt update \
    && apt -yy upgrade \
    && apt -yy install curl

RUN curl -sL https://get.keptn.sh | bash

FROM alpine
COPY --from=builder /usr/local/bin/keptn /usr/local/bin
