FROM alpine:latest
MAINTAINER hundredlee <hundred9411@gmail.com>

# Install packages from testing repo's
RUN apk --no-cache add bash redis\
    --repository http://dl-cdn.alpinelinux.org/alpine/edge/main/ \
    --repository http://dl-cdn.alpinelinux.org/alpine/edge/testing/

CMD ["/bin/bash"]
ENTRYPOINT ["/bin/sh", "-c"]