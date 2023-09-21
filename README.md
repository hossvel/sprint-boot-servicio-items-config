# sprint-boot-servicio-configurations
# configuracuo de rabbitmq
# DOCKER
## levantando mysql desde imagen para microservicio productos: 
docker run -d -p 3306:3306 --name microservicios-mysql8 --network sprintcloud -e MYSQL_ROOT_PASSWORD=sasa -e MYSQL_DATABASE=db_sprintboot_cloud mysql:8.1.0

## levantando postgres desde imagen para microservicio :
docker run -d -p 5432:5432 --name microservicios-postgres16 --network sprintcloud -e POSTGRES_PASSWORD=sasa -e POSTGRES_DB=db_sprintboot_cloud postgres:16.0-alpine

# DOCKER rabbitMQ
## levantar la parte backend y frontend
## docker run -d -p 5672:5672 -p 15672:15672 --name microservicio-rabbitmq312 --network sprintcloud rabbitmq:3.12-management-alpine

# DOCKER ZIPKIN - levantar server 
## generar imagen: docker build -t zipkin-server:v1 .
## creando red: docker network create sprintcloud
## levantando servicio: docker run -d -p 9411:9411 --name zipkin-server --network sprintcloud -e RABBIT_ADDRESSES=microservicio-rabbitmq312:5672 -e STORAGE_TYPE=mysql -e MYSQL_USER=zipkin -e MYSQL_PASS=zipkin -e MYSQL_HOST=microservicios-mysql8  zipkin-server:v1
