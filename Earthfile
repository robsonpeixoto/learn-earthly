VERSION 0.6
FROM golang:1.18-alpine3.16
WORKDIR /app

deps:
  COPY go.mod go.sum ./
  RUN go mod download
  SAVE ARTIFACT go.mod AS LOCAL go.mod
  SAVE ARTIFACT go.sum AS LOCAL go.sum

build:
  FROM +deps
  COPY main.go .
  RUN go build -o learn-earthly main.go
  SAVE ARTIFACT learn-earthly /learn-earthly AS LOCAL learn-earthly

docker:
  FROM alpine:3.16
  WORKDIR /app
  COPY +build/learn-earthly .
  ARG EARTHLY_TARGET_TAG_DOCKER
  LABEL org.opencontainers.image.description="learn how to use eartlhy"
  SAVE IMAGE --push ghcr.io/robsonpeixoto/learn-earthly:${EARTHLY_TARGET_TAG_DOCKER}
