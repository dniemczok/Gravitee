# Gravitee


sudo sysctl -w vm.max_map_count=262144

vi /etc/sysctl.conf
vm.max_map_count=262144

mkdir /opt/DOC

mkdir /opt/DOC/gravitee

cd /opt/DOC/gravitee

mkdir -p config

# v.2.x


curl -L -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/docker-compose.yml

curl -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/.env

cd config && { curl -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/config/nginx.conf ; cd -; }

docker-compose pull

### Zmień w docker-compose.yml

- MGMT_API_URL=http://Adress IP:${NGINX_PORT}/am
- MGMT_UI_URL=http://Adres IP:${NGINX_PORT}/am/ui


docker-compose up

###

ONTAINER ID        IMAGE                            COMMAND                  CREATED             STATUS              PORTS                NAMES
622717cdfcd4        nginx:1.16-alpine                "nginx -g 'daemon of…"   2 hours ago         Up 2 hours          0.0.0.0:80->80/tcp   gio_am_nginx
f10c450081a0        graviteeio/am-management-ui:2    "sh /run.sh"             2 hours ago         Up 2 hours          80/tcp               gio_am_webui
a11fd2c1e84a        graviteeio/am-gateway:2          "./bin/gravitee"         5 hours ago         Up 2 hours          8092/tcp             gio_am_gateway
5298150bb9d4        graviteeio/am-management-api:2   "./bin/gravitee"         5 hours ago         Up 2 hours          8093/tcp             gio_am_management
9686903ebbe4        mongo:3.4                        "docker-entrypoint.s…"   5 hours ago         Up 2 hours          27017/tcp            gio_am_mongodb

ansadmin@fossil:~$ docker images
REPOSITORY                     TAG                 IMAGE ID            CREATED             SIZE
graviteeio/am-management-ui    2                   8d740594c419        2 weeks ago         43.8MB
graviteeio/am-management-api   2                   a31098c2d5da        2 weeks ago         223MB
graviteeio/am-gateway          2                   155ed651b420        2 weeks ago         211MB
mongo                          3.4                 f76f959b2a49        8 months ago        431MB
nginx                          1.16-alpine         5fad07aba15a        8 months ago        21.8MB

###


# v.3.x

sysctl -w vm.max_map_count=262144


mkdir data-elasticsearch

chmod g+rwx data-elasticsearch

chgrp 0 data-elasticsearch


curl -L https://raw.githubusercontent.com/gravitee-io/gravitee-docker/master/apim/3.x/docker-compose.yml -o "docker-compose.yml"

docker-compose pull

docker-compose up
