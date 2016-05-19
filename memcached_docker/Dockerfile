
#
# Memcached Dockerfile
#
# https://github.com/hostelix/imagenes_docker/memcached_docker
#

#Usamos como base ubuntu i686
FROM i686/ubuntu


MAINTAINER Israel Lugo - Hostelix

# Actualización de la lista de fuentes del repositorio de aplicaciones por defecto
RUN apt-get update

# Instalar Memcached
RUN apt-get install -y memcached nano vim

# Puerto para exponer (por defecto: 11211)
EXPOSE 11211

# Comando Memcached por defecto con algunos argumentos
CMD ["-u", "root", "-m", "128"]

# Establece el usuario para ejecutar el demonio Memcached
USER daemon

# Establece el punto de entrada para los binarios de Memcached
ENTRYPOINT memcached
