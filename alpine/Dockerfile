FROM alpine

# Install dependencies
RUN apk add \
    gcc \
    gnupg \
    make \
    musl-dev \
    openssl-dev \
    openssl-libs-static file

COPY build.sh /build.sh
RUN ./build.sh

FROM alpine
COPY --from=0 /out/curl /usr/local/bin
