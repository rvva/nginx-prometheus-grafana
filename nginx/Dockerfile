FROM nginx:1.21.3-alpine as base

FROM base as dev

# generate self segined certificate for testing pruposes
RUN apk update && \
    apk add --no-cache openssl && \
    openssl req -x509 -nodes -days 365 \
    -subj "/C=PL/ST=lubelskie/L=Lublin/O=github-rvva/OU=dev/CN=rvva" \
    -newkey rsa:4096 -keyout /etc/ssl/private/selfsigned.key \
    -out /etc/ssl/certs/selfsigned.crt
