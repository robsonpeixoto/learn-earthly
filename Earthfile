VERSION 0.6
FROM golang:1.13-alpine3.11

build:
  COPY main.go .
  RUN go build main.go
  SAVE ARTIFACT main AS LOCAL main
