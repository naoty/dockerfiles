FROM debian:wheezy
MAINTAINER Naoto Kaneko <naoty.k@gmail.com>

# Essentials
RUN apt-get update && \
    apt-get install -y \
        procps && \
    apt-get clean

# User
RUN useradd -m -s /bin/bash naoty
