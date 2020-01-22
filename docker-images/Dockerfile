FROM ubuntu

RUN apt update && apt install apache2 -y

#LABEL es para poder dejar pequeñas descripciones
LABEL version=1.0
LABEL author="Ing. Mario Guadalupe Sánchez Silva"

# SIrve para indicar el directorio donde se va a ejecutar
WORKDIR /var/www/html

#copia el contenido y ADD hace lo mismo pero igualmente puede agregar URLs dentro de un archivo
COPY focus-free1 .

#Este es para pocer hacer variables de entorno a las cuales puede acceder el SO
ENV contenido mariossan
RUN echo "$contenido" > /var/www/html/prueba.html

#User para saber quien lo ejecuta
RUN echo "$(whoami)" > /var/www/html/user1.html
RUN useradd mariossan
# RUN chown -R mariossan /var/www/html 
# USER mariossan
# RUN echo "$(whoami)" > /var/www/html/user2.html

#mantener data persistente dentro del contenedor
VOLUME /var/www/html

#Este es de los principales para que apache quede corriendo en background
#CMD apachectl -D FOREGROUND
COPY run.sh /run.sh
CMD sh /run.sh
