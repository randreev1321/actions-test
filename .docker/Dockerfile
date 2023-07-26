FROM alpine AS builder

RUN set -e; case "$(apk --print-arch)" in \
      x86_64) export ARCH='amd64' ;; \
      aarch64) export ARCH='arm64' ;; \
      armv7) export ARCH='arm' ;; \
    esac; \
    echo $ARCH; \
    wget -O /tmp/file.tgz "https://github.com/randreev1321/actions-test/releases/download/$VERSION/file-$ARCH.tar.gz"; \
    tar xf /tmp/file.tgz


FROM scratch

COPY --from=builder /file /file
