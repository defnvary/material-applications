FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN apk add build-base

ENV REQUEST_ORIGIN=http://localhost/api

RUN go build

RUN go test ./...

CMD ["./server"]
