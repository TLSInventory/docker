FROM nginx:1.17-alpine

# The following commands might fail, when docker is ran inside another docker, or in VM.
# https://github.com/gliderlabs/docker-alpine/issues/307
RUN apk update
RUN apk add openssl


RUN openssl req -x509 -newkey rsa:4096 -keyout /etc/ssl/private/key.pem -out /etc/ssl/private/cert.pem -days 3650 -passout pass:xxxx -subj '/CN=localhost'

RUN rm /etc/nginx/conf.d/default.conf
COPY nginx.conf /etc/nginx/conf.d/main-proxy.conf
COPY cloudflare_real_ips.conf /etc/nginx/cloudflare_real_ips.conf
COPY keys.pass /etc/ssl/private/keys.pass
