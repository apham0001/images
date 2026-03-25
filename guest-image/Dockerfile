FROM containerssh/agent:latest AS agent

FROM ubuntu:24.04

RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -fuy upgrade && \
    DEBIAN_FRONTEND=noninteractive apt-get -fuy install ssh && \
    apt-get -y autoremove && apt-get -y clean && \
    rm -rf /var/lib/apt/lists/*

COPY --from=agent /usr/bin/containerssh-agent /usr/bin/containerssh-agent

CMD ["/bin/bash"]
SHELL ["/bin/bash"]
