FROM golang:alpine AS build

WORKDIR /usr/src/go/hello

COPY ./ ./

RUN go build -ldflags "-s -w" -o /go-fullcycle-app

FROM scratch

WORKDIR /

COPY --from=build /go-fullcycle-app /go-fullcycle-app

EXPOSE 8080

ENTRYPOINT [ "/go-fullcycle-app" ]

CMD ["/go-fullcycle-app"]