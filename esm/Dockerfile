FROM golang:1.18 AS build

RUN apt-get update -y && apt-get install -y xz-utils
RUN useradd -u 1000 -m esm
RUN mkdir /esm && chown esm:esm /esm
RUN git clone https://github.com/ije/esm.sh /esm/esm.sh

COPY ./config.json /esm/config.json

USER esm
WORKDIR /esm
RUN go build -o bin/esmd esm.sh/main.go

ENTRYPOINT ["/esm/bin/esmd", "--config", "/esm/config.json"]