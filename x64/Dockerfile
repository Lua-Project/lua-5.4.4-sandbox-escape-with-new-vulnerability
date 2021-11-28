FROM ubuntu:18.04

RUN mkdir -p /LUA

WORKDIR /LUA
COPY ./ /LUA

RUN apt-get update
RUN apt-get install -y build-essential
RUN apt-get -y install libreadline-dev
RUN apt-get -y install manpages-dev
RUN apt-get -y install git 

RUN git clone https://github.com/lua/lua.git
WORKDIR /LUA/lua
RUN make
