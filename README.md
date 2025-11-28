# Proyecto Flask con Redis y Docker

Este es un proyecto de ejemplo simple que utiliza Flask y Redis. Está configurado para ser ejecutado con Docker y Docker Compose, sirviendo como una práctica básica para entender cómo orquestar contenedores.

La aplicación web es un contador de visitas que utiliza Redis para persistir el número de visitas.

## Requisitos

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

## Cómo ejecutar el proyecto

1. Clona este repositorio:
   ```bash
   git clone <URL-del-repositorio>
   cd <nombre-del-directorio>
   ```

2. Levanta los servicios utilizando Docker Compose:
   ```bash
   docker-compose up --build
   ```
   Esto construirá la imagen para la aplicación Flask y levantará dos contenedores: uno para la aplicación web y otro para la base de datos Redis.

3. Abre tu navegador y visita `http://localhost:5000`.

Deberías ver un mensaje que dice "Esta página ha sido visitada X veces.", donde X se incrementará cada vez que recargues la página.

## Funcionamiento

- **`app.py`**: Contiene la lógica de la aplicación Flask. Se conecta a Redis, obtiene el contador actual, lo incrementa en uno y lo guarda de nuevo. Luego, renderiza el resultado.
- **`Dockerfile`**: Define la imagen de Docker para la aplicación Flask. Instala las dependencias de Python (`Flask` y `redis`) y establece el comando para iniciar la aplicación.
- **`docker-compose.yaml`**: Orquesta los contenedores. Define dos servicios:
    - `web`: La aplicación Flask.
    - `redis`: La base de datos Redis.
  La aplicación Flask puede comunicarse con el servicio de Redis utilizando el nombre de host `redis`.

## Estructura del Proyecto

```
.
├── app.py                # Aplicación principal de Flask
├── Dockerfile            # Define la imagen de la aplicación
├── requirements.txt      # Dependencias de Python
└── docker-compose.yaml   # Orquestación de los contenedores
```
