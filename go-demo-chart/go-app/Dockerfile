FROM golang:1.21.0 AS builder

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download

COPY *.go ./

RUN CGO_ENABLED=0 GOOS=linux go build -o demo-gin-app

FROM alpine:latest

COPY --from=builder /app/demo-gin-app .

EXPOSE 8080

CMD ["./demo-gin-app"]
