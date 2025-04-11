# Use a imagem original como base
FROM docker.osgeo.org/geoserver:2.25.3

# Defina as variáveis de ambiente
ENV ROOT_WEBAPP_REDIRECT=true
ENV GEOSERVER_ADMIN_PASSWORD=admin
ENV INSTALL_EXTENSIONS=true
# ENV STABLE_EXTENSIONS="control-flow,css,db2,excel,gdalh2,mbstyle,monitor,mysql,ogr-wfs,ogrwps,oracle,params-extractor,printing,sqlserver,vectortiles,wps,postegresql,ogr-datastore,geopkg,csv,shapefile,wps-remote,gwc-distributed,gwc-mobile,importer,notification,backup-restore,cas,authkey"
# (default false)
#ENV CORS_ENABLED=true 
#(default *)
#ENV CORS_ALLOWED_ORIGINS=*
#(default GET,POST,PUT,DELETE,HEAD,OPTIONS)
#ENV CORS_ALLOWED_METHODS=GET,POST,PUT,HEAD,OPTIONS
#(default *)
#ENV CORS_ALLOWED_HEADERS=*
#(default false)
#ENV CORS_ALLOW_CREDENTIALS=false

# subistituicao web.xml - CORS
# Defina o diretório de trabalho
WORKDIR /opt/apache-tomcat-9.0.89/webapps/geoserver/WEB-INF

# Copie o novo arquivo web.xml para o contêiner
COPY web.xml ./web.xml

# substituir server.xml e keystore.jks
WORKDIR /opt/config
COPY server.xml ./server.xml
COPY server-https.xml ./server-https.xml
COPY keystore.jks ./keystore.jks

# Comando para iniciar o GeoServer (este já está no entrypoint da imagem base)
# Você pode deixar a linha abaixo se precisar modificar algo, caso contrário, ela não é necessária.
# CMD ["catalina.sh", "run"]

