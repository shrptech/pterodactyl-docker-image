FROM quay.io/parkervcp/pterodactyl-images:debian_source
USER root
RUN apt-get update
RUN apt-get dist-upgrade -y
RUN apt-get install -y libpulse0 libpulse-dev

COPY ./debian/entrypoint.sh /entrypoint.sh
USER container
