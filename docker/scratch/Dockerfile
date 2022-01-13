FROM golang:1.17 as builder
ENV CGO_ENABLED=0

COPY . /app
WORKDIR /app

RUN go build -ldflags "-s -w" -o /http-echo

FROM scratch
COPY --from=builder /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/
COPY --from=builder /http-echo /
ENTRYPOINT ["/http-echo"]
