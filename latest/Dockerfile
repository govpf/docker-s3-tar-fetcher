FROM alpine:3.23

LABEL govpf.fromimage="alpine:3.23"
LABEL govpf.category="utility"
LABEL description="S3 archive fetcher"

RUN apk --no-cache --update add \
    bash \
    ca-certificates \
    grep \
    pigz \
    tar \
    tzdata \
    python3 \
    py3-pip \
    && python3 -m venv /opt/awscli \
    && /opt/awscli/bin/pip install --no-cache-dir "awscli~=1.43" \
    && ln -s /opt/awscli/bin/aws /usr/local/bin/aws \
    && rm -rf /var/cache/apk/*

# Required to enable the helper to load IRSA roles
ENV AWS_SDK_LOAD_CONFIG=1

COPY latest/fetcher /fetcher

ENTRYPOINT ["/fetcher"]