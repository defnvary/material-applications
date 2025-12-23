FROM golang:1.16-alpine

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN apk add --no-cache build-base && adduser -D backend-user && chown backend-user -R .

USER backend-user

ENV REQUEST_ORIGIN=http://localhost/api

RUN go build && go test ./...

CMD ["./server"]
