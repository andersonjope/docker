FROM golang:alpine AS build

WORKDIR /usr/src/go/hello

COPY ./ ./
RUN go mod download && go mod verify

COPY . .
RUN go build -o /go-fullcycle-app

FROM gcr.io/distroless/static-debian11

WORKDIR /

COPY --from=build /go-fullcycle-app /go-fullcycle-app

EXPOSE 8080

USER nonroot:nonroot

ENTRYPOINT [ "/go-fullcycle-app" ]