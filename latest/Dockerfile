FROM alpine:3.13
LABEL description="S3 archive fetcher"

RUN apk --no-cache --update add \
  ca-certificates \
  grep \
  pigz \
  tar

# Required to enable the helper to load IRSA roles
ENV AWS_SDK_LOAD_CONFIG=1

# AWScli
RUN apk --no-cache --update add python3 py3-pip \
    && pip install awscli~=1.18 \
    && apk --purge -v del py-pip

COPY latest/fetcher /fetcher

ENTRYPOINT [ "/fetcher" ]
