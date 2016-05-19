#
# Yii 1 + Nginx Dockerfile
#
# https://github.com/hostelix/imagenes_docker/yii_docker
#

#Usamos como base ubuntu i686
FROM i686/ubuntu


MAINTAINER Israel Lugo - Hostelix

# Actualizamos los repositorios
RUN  apt-get update

# Instalamos ngnix y php con sus dependencias
RUN  apt-get install -y\
		git \	
        curl \
        nginx \
        php5-fpm \
        php5-curl \
        php5-cli \
        php5-gd \
        php5-intl \
        php5-mcrypt \
        php5-mysql \
        php5-pgsql \ 
        php5-xsl \
        php-apc \
        nano \
        wget\
        unzip && \
  	rm -rf /var/lib/apt/lists/* && \
  	echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  	chown -R www-data:www-data /var/lib/nginx


#descargamos el framework yii y lo guardamos en la carpeta temporal
RUN wget https://github.com/yiisoft/yii/releases/download/1.1.17/yii-docs-1.1.17.467ff50.zip -O /tmp/yii_framework.zip

#Extraemos el .zip en la carpeta publica que accede nginx
RUN unzip /tmp/yii_framework.zip -d /usr/share/nginx/html/yii/

#Eliminamos el archivo .zip
RUN rm /tmp/yii_framework.zip 

#Creamos la app de yii
RUN cd /usr/share/nginx/html/yii/framework/
RUN ./yiic webapp ../app_yii

# iniciamos el servidor de nginx
RUN /etc/init.d/nginx start

# iniciamos el php-fpm
RUN /etc/init.d/php5-fpm start

# Montamos las carpetas necesarias
VOLUME ["/etc/nginx/sites-enabled", "/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Agregamos la configuracion del nginx
ADD default /etc/nginx/sites-available/default

# Definimos el espacio de trabajo
WORKDIR /usr/share/nginx/html/yii/

# Ejecuatamos
CMD ["nginx"]

# Exponemos el puerto por el que se comunicara con el SO
EXPOSE 8001
