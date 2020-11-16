FROM golang:1.15-alpine as builder
WORKDIR /src

# restore dependencies
COPY go.mod go.sum ./
RUN go mod download

COPY . .
RUN go build -gcflags='-N -l' -o /goserver .

FROM alpine as release

COPY --from=builder /goserver /goserver
EXPOSE 8080
ENTRYPOINT ["/goserver"]