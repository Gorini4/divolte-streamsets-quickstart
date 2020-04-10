# ClickStream example with Divolte and StreamSets

## How to install

1. Install [Docker Compose](https://docs.docker.com/compose/install/)
2. Clone this repository with `git clone`
3. Go to repository folder
4. Spin up containers with `docker-compose up`

Default credentials for StreamSets: admin / admin

## Troubleshooting

1. Check your container status with `docker ps -a`
2. If you see failed contaiers use `docker logs (container_name)`
3. Check logs for following errors:

### Streamsets: java.io.FileNotFoundException: /data/sdc.id (Permission denied)

Set permissions `chmod 777 sdc-data`

### StreamSets: Connection to node -1 could not be established. Broker may not be available

Check next error in Kafka container.

### Kafka: exited: kafka (exit status 1; not expected)

Check Docker memory limits (8 Gb worked for me).

### Streamsets: Configuration of maximum open file limit is too low: 1024 (expected at least 32768)

Add ulimits configuration in docker-compose.yml: https://docs.docker.com/compose/compose-file/compose-file-v2/#ulimits
