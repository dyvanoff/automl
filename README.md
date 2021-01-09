# AutoML - H2O

## Integrantes

- Leonardo Palacios
- Marcelo Tisera
- Dario Yvanoff



## Setup
- Tener instalado Java JRE
- Instalar H20 Flow a partir de los pasos del sitio oficial de [H2O.ai](http://h2o-release.s3.amazonaws.com/h2o/rel-zermelo/3/index.html)

- O directamente descargar desde aqui [H20](http://h2o-release.s3.amazonaws.com/h2o/rel-zermelo/3/h2o-3.32.0.3.zip), descomprimir y luego ejecutar el .jar


```bash
cd ~/Downloads
unzip h2o-3.32.0.3.zip
cd h2o-3.32.0.3
java -jar h2o.jar
```

> Para acceder a la H2O Flow ingresar a [http://localhost:54321/](http://localhost:54321/)

## Instalacion

1) Ubicarse en la carpeta root (/catpill) y ejecutar
```bash
sudo docker-compose build
sudo docker-compose up -d
```


## Usage

```bash
curl --location --request POST 'http://<server_ip>:8080/predict' \
--form 'File=@"/path/to/file.csv"'
```

## Configuracion
- Para modificar el puerto desde donde escucha el servicio (por defecto `8080`), modificar el archivo `docker-compose.yml`

```
nginx:
    container_name: nginx
    restart: always
    build: ./nginx
    networks:
      - apinetwork
    ports:
      - "8080:8080" <--HERE!
```
