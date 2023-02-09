FROM golang:alpine AS builder

LABEL stage=gobuilder

ENV CGO_ENABLED 0

RUN apk update --no-cache && apk add --no-cache upx

WORKDIR /build

ADD .. .
RUN go mod download
RUN go build -ldflags="-s -w" -o /app/file-go . && upx -9 -o /app/file /app/file-go


FROM scratch

WORKDIR /app
COPY --from=builder /app/file /file
