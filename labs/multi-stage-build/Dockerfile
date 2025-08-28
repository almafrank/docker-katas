FROM golang:1.19 AS builder
WORKDIR /app
COPY . /app
RUN go mod download && go mod verify
RUN cd /app && go build -o goapp
ENTRYPOINT ./goapp

# final stage
FROM scratch
WORKDIR /app
COPY --from=builder /app/goapp/ app/
CMD ["/app/goapp"]

