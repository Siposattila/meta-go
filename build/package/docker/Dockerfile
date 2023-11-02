# syntax=docker/dockerfile:1

FROM golang:1.19

WORKDIR /app

COPY go.mod go.sum ./
RUN go mod download

COPY cmd ./cmd
COPY .env ./cmd/meta
COPY internal ./internal
COPY pkg ./pkg
COPY test ./test

WORKDIR /app/cmd/meta
RUN CGO_ENABLED=0 GOOS=linux go build -o app.meta

CMD ["./app.meta"]
