# Этап 1: Сборка приложения
FROM golang:1.16 AS builder
WORKDIR /app
COPY go.mod go.sum .
RUN go mod download
COPY . .
RUN CGO_ENABLED=0 GOOS=linux go build .

# Этап 2: Запуск приложения
FROM alpine:3.20
WORKDIR /app
COPY --from=builder /app/pig .
COPY --from=builder /app/resources/index.html /app/resources/index.html

EXPOSE 8000
CMD ["./pig"]
