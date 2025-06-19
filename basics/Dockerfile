FROM golang:1.24 AS builder

WORKDIR /app

COPY . .

RUN go mod download

RUN GOOS=linux GOARCH=amd64 CGO_ENABLED=0 go build -o application cmd/app/main.go

FROM alpine AS serve

COPY --from=builder /app/application .

ENV HTTP_SERVER_PORT=8080

ENTRYPOINT ["./application"]

CMD [""]
