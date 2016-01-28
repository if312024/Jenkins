FROM debian:jessie

MAINTAINER Roy Inganta Ginting <roy.i.ginting@gdplabs.id>

COPY nginx_signing.key /tmp/nginx_signing.key
RUN apt-key add /tmp/nginx_signing.key
#RUN apt-key adv --keyserver pgp.mit.edu --recv-keys 573BFD6B3D8FBC641079A6ABABF5BD827BD9BF62
RUN echo "deb http://nginx.org/packages/debian/ jessie nginx" >> /etc/apt/sources.list

#ENV NGINX_VERSION 1.6.2-1~wheezy
ENV DEBIAN_FRONTEND noninteractive

RUN apt-get update && apt-get install -y nginx curl #=${NGINX_VERSION} curl
ADD nginx.conf /etc/nginx/nginx.conf
ADD http-https-redirect /etc/nginx/sites-available/http-https-redirect
RUN mkdir -p /etc/nginx/sites-enabled
RUN rm /etc/nginx/conf.d/default.conf
RUN ln -sf /etc/nginx/sites-available/http-https-redirect /etc/nginx/sites-enabled/

VOLUME [ "/var/log/nginx" ]

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
