FROM golang:alpine AS build

WORKDIR /usr/src/go/hello

COPY ./ ./

RUN CGO_ENABLED=0 GOOS=linux go build -o /go-fullcycle-app

FROM gcr.io/distroless/static-debian12

WORKDIR /

COPY --from=build /go-fullcycle-app /go-fullcycle-app

EXPOSE 8080

USER nonroot:nonroot

ENTRYPOINT [ "/go-fullcycle-app" ]