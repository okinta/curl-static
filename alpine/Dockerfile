FROM alpine

# Install dependencies
RUN apk add \
    file \
    gcc \
    gnupg \
    make \
    musl-dev \
    openssl-dev \
    openssl-libs-static

# Build curl
COPY build.sh /build.sh
RUN ./build.sh

# Prepare for distribution
RUN mkdir -p /curl/usr/local/bin \
    && cp /out/curl /curl/usr/local/bin

FROM alpine
COPY --from=0 /curl /curl
