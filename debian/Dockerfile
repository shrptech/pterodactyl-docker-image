FROM ghcr.io/matthewpi/images:debian
USER root
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install -y libpulse0 libpulse-dev libatomic1 libc6

USER container
