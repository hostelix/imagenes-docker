
#
# Nginx Dockerfile
#
# https://github.com/hostelix/imagenes_docker/ngnix_docker
#

#Usamos como base ubuntu i686
FROM i686/ubuntu


MAINTAINER Israel Lugo - Hostelix

# Actualizamos los repositorios
RUN  apt-get update

# Instalamos ngnix
RUN  apt-get install -y php5-fpm nano git nginx && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

# Montamos las carpetas necesarias
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Definimos el espacio de trabajo
WORKDIR /etc/nginx

# Exponemos el puerto por el que se comunicara con el SO
EXPOSE 8000
#EXPOSE 443
