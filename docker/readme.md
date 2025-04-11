# GEOSERVER 

Para substituir o arquivo web.xml na imagem Docker docker.osgeo.org/geoserver:2.25.3 usando um Dockerfile, você pode seguir os seguintes passos:

1. *Crie um Dockerfile*: Esse arquivo vai ser responsável por criar uma nova imagem baseada na imagem original do GeoServer, mas com o web.xml modificado.

2. *Copie o novo `web.xml*: Você vai usar o comando COPY para adicionar o novo web.xml na localização correta dentro do contêiner.

Aqui está um exemplo básico de como pode ser o seu `Dockerfile`:

``` Dockerfile
# Use a imagem original como base
FROM docker.osgeo.org/geoserver:2.25.3

# Defina o diretório de trabalho
WORKDIR /usr/local/tomcat/webapps/geoserver/WEB-INF

# Copie o novo arquivo web.xml para o contêiner
COPY web.xml web.xml

# Comando para iniciar o GeoServer (este já está no entrypoint da imagem base)
# Você pode deixar a linha abaixo se precisar modificar algo, caso contrário, ela não é necessária.
# CMD ["catalina.sh", "run"]
```

Construa a imagem: Depois de criar o Dockerfile e colocar o novo web.xml na mesma pasta, você pode construir a nova imagem Docker.
```bash
$ docker build -t my-geoserver:2.25.3 .
```

Execute o contêiner: Após construir a imagem, você pode rodar um contêiner com a nova imagem:
```bash
docker run -d -p 8080:8080 my-geoserver:2.25.3
```
Isso criará um contêiner com o web.xml substituído, permitindo que você rode o GeoServer com as configurações específicas que deseja.
