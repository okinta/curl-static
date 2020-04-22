ARG UBUNTU_VERSION=18.04
FROM ubuntu:$UBUNTU_VERSION

# Install dependencies
RUN apt-get update && apt-get install -y wget
RUN apt-get install -y gpg
RUN apt-get install -y xz-utils
RUN apt-get install -y build-essential
RUN apt-get install -y libssl-dev

# Build curl
ENV LIBS=-ldl
COPY build.sh /build.sh
RUN ./build.sh

# Prepare for distribution
RUN mkdir -p /curl/usr/local/bin \
    && cp /out/curl /curl/usr/local/bin \
    && mkdir -p /curl/etc/ssl/certs \
    && cp /etc/ssl/certs/ca-certificates.crt /curl/etc/ssl/certs/ca-certificates.crt

FROM ubuntu:$UBUNTU_VERSION
COPY --from=0 /curl /curl
