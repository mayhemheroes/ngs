FROM --platform=linux/amd64 ubuntu:20.04 as builder

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y build-essential

COPY . /repo
WORKDIR /repo
RUN DEBIAN_FRONTEND=noninteractive ./install.sh

FROM ubuntu:20.04 as package
RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -y libgc-dev libjson-c-dev
COPY --from=builder /usr/local/bin/ngs /
