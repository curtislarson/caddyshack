FROM golang:1.18 AS build

RUN apt-get update -y && apt-get install -y xz-utils

RUN useradd -u 1000 -m esm

RUN mkdir -p /esm.sh && chown esm:esm /esm.sh

WORKDIR /esm.sh

RUN git clone https://github.com/ije/esm.sh ./

COPY ./config.json ./config.json

USER esm

RUN go build -o ./bin/esmd ./main.go

ENTRYPOINT ["/esm.sh/bin/esmd", "--config", "./config.json"]