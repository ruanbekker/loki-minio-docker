# https://hasura.io/blog/the-ultimate-guide-to-writing-dockerfiles-for-go-web-apps-336efad7012c/
FROM golang:1.8.5-jessie as builder

RUN apt-get update && apt-get install xz-utils -y \
    && rm -rf /var/lib/apt/lists/*

ADD https://github.com/upx/upx/releases/download/v3.94/upx-3.94-amd64_linux.tar.xz /usr/local

RUN xz -d -c /usr/local/upx-3.94-amd64_linux.tar.xz | \
    tar -xOf - upx-3.94-amd64_linux/upx > /bin/upx && \
    chmod a+x /bin/upx
RUN go get github.com/golang/dep/cmd/dep

WORKDIR /go/src/app
ADD Gopkg.toml Gopkg.toml
ADD Gopkg.lock Gopkg.lock

RUN dep ensure --vendor-only
ADD src src
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o main src/main.go
RUN strip --strip-unneeded main
RUN upx main

FROM scratch
WORKDIR /root
COPY --from=builder /go/src/app/main .

CMD ["./main"]
