VERSION 0.6
FROM golang:1.13-alpine3.11

build:
  COPY main.go .
  RUN go build main.go
  ARG EARTHLY_TARGET_TAG_DOCKER
  LABEL org.opencontainers.image.description="learn how to use eartlhy"
  SAVE IMAGE --push ghcr.io/robsonpeixoto/learn-earthly:${EARTHLY_TARGET_TAG_DOCKER}

