FROM quay.io/parkervcp/pterodactyl-images:debian_source
USER root
RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y libpulse0 libpulse-dev

USER container
