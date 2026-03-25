FROM golang:1.25-alpine AS builder

ARG AGENT_VERSION=main
ARG TARGETARCH

RUN apk add --no-cache git

WORKDIR /build
RUN git clone --depth 1 --branch ${AGENT_VERSION} https://github.com/ContainerSSH/agent.git . && \
    go generate ./... && \
    CGO_ENABLED=0 GOOS=linux GOARCH=${TARGETARCH} go build -o /usr/bin/containerssh-agent .

FROM scratch
COPY --from=builder /usr/bin/containerssh-agent /usr/bin/containerssh-agent
ENTRYPOINT ["/usr/bin/containerssh-agent"]
