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

FROM ubuntu:$UBUNTU_VERSION
COPY --from=0 /out/curl /usr/local/bin
COPY --from=0 /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/ca-certificates.crt
