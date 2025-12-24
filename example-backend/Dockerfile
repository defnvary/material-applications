FROM golang:1.16-alpine AS build-stage

EXPOSE 8080

WORKDIR /usr/src/app

COPY . .

RUN apk add --no-cache build-base && adduser -D backend-user && chown backend-user -R .

USER backend-user

ENV REQUEST_ORIGIN=http://localhost/api

RUN CGO_ENABLED=0 go build && go test ./...

#CMD ["./server"]

FROM scratch

WORKDIR /usr/src/app

COPY --from=build-stage /etc/ssl/certs/ca-certificates.crt /etc/ssl/certs/

COPY --from=build-stage /etc/passwd /etc/passwd

COPY --from=build-stage /usr/src/app/server .

EXPOSE 8080

USER backend-user

ENTRYPOINT ["./server"]
