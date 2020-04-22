FROM alpine
COPY build.sh /build.sh
RUN ./build.sh

FROM alpine
COPY --from=0 /out/curl /usr/local/bin
