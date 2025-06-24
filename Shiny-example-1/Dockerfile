# Imagen base con R y Shiny Server preinstalado
FROM rocker/shiny:latest

# Instala paquetes del sistema requeridos
RUN apt-get update && apt-get install -y \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libharfbuzz-dev \
    libfribidi-dev \
    && rm -rf /var/lib/apt/lists/*

# Copia el archivo app.r al directorio de la app
COPY app.r /srv/shiny-server/

# Instala paquetes de R necesarios
RUN R -e "install.packages(c('shiny', 'bslib', 'dplyr', 'ggplot2', 'ggExtra', 'readr'))"

# Cambia permisos (Shiny Server corre como shiny)
RUN chown -R shiny:shiny /srv/shiny-server

# Expone el puerto de Shiny por defecto
EXPOSE 3838

# El contenedor arranca shiny-server automáticamente (CMD ya está en la imagen base)
