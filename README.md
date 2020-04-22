# README

Provides statically linked curl binaries for containers. This provides the
advantage of allowing usage of curl without installing unnecessary packages or
using package management systems.

## Usage

Containers are published with the compiled curl binaries. As an example, to
pull curl inside your container, you can use the following in your Dockerfile:

    FROM ubuntu
    COPY --from=okinta/curl-static:ubuntu /curl /

`curl` will now be available for use within your container.

## Known Bugs

* Currently if you try to set curl to follow redirects via `curl -L`, it
results in a segmentation fault

## Development

### Alpine

To build for Alpine, run:

    docker build -t okinta/curl-static:alpine -f alpine/Dockerfile .

### Ubuntu

To build for Ubuntu, run:

    docker build -t okinta/curl-static:ubuntu -f ubuntu/Dockerfile .
