# Etapa de build
FROM golang:latest AS builder

LABEL maintainer="Arthur"
LABEL env="production"

WORKDIR /app

COPY . .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 go build -o server main.go

# Etapa final - imagem mínima
FROM scratch

COPY --from=builder /app/server /server

ENTRYPOINT ["/server"]
CMD ["/8080"]
