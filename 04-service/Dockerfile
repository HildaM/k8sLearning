# Dockerfile
FROM golang:1.19.3 AS builder
RUN mkdir /src
ADD . /src
WORKDIR /src

RUN go env -w GO111MODULE=auto && \
    go build -o main .

FROM registry.cn-shenzhen.aliyuncs.com/quandocker/sotaquan:base-debain10

WORKDIR /

COPY --from=builder /src/main /main
EXPOSE 3000
ENTRYPOINT ["/main"]
