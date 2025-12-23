FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN apk add build-base

RUN adduser -D backend-user

RUN chown backend-user -R .

USER backend-user

ENV REQUEST_ORIGIN=http://localhost/api

RUN go build

RUN go test ./...

CMD ["./server"]
