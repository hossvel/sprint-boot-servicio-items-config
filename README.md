# sprint-boot-servicio-configurations
# configuracuo de rabbitmq
# DOCKER
## levantando mysql desde imagen para microservicio productos: 
docker run -d -p 3306:3306 --name microservicios-mysql8 --network sprintcloud -e MYSQL_ROOT_PASSWORD=sasa -e MYSQL_DATABASE=db_sprintboot_cloud mysql:8.1.0

## levantando postgres desde imagen para microservicio :
docker run -d -p 5432:5432 --name microservicios-postgres16 --network sprintcloud -e POSTGRES_PASSWORD=sasa -e POSTGRES_DB=db_sprintboot_cloud postgres:16.0-alpine