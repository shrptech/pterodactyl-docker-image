FROM debian:bullseye-slim

ENV DEBIAN_FRONTEND noninteractive

## add container user
RUN useradd -m -d /home/container -s /bin/bash container

RUN ln -s /home/container/ /nonexistent

ENV USER=container HOME=/home/container

## update base packages
RUN apt update \
 && apt upgrade -y

## install dependencies
RUN apt install -y gcc g++ libgcc1 libc++-dev gdb libc6 git wget curl tar zip unzip binutils xz-utils liblzo2-2 cabextract iproute2 net-tools netcat telnet libatomic1 libsdl1.2debian libsdl2-2.0-0 \
    libfontconfig icu-devtools libunwind8 libssl-dev sqlite3 libsqlite3-dev locales ffmpeg gnupg2 apt-transport-https software-properties-common ca-certificates tzdata \
    libz-dev rapidjson-dev

## configure locale
RUN update-locale lang=en_US.UTF-8 \
 && dpkg-reconfigure --frontend noninteractive locales

WORKDIR /home/container

COPY ./debian/entrypoint.sh /entrypoint.sh
CMD ["/bin/bash", "/entrypoint.sh"]

## install rcon
RUN cd /tmp/ \
 && curl -sSL https://github.com/gorcon/rcon-cli/releases/download/v0.9.0/rcon-0.9.0-amd64_linux.tar.gz > rcon.tar.gz \
 && tar xvf rcon.tar.gz \
 && mv rcon-0.9.0-amd64_linux/rcon /usr/local/bin/

COPY ./entrypoint.sh /entrypoint.sh

RUN apt-get install -y libpulse0 libpulse-dev
USER container
ENV         HOME /home/container
