# Gravitee


sudo sysctl -w vm.max_map_count=262144

vi /etc/sysctl.conf
vm.max_map_count=262144

mkdir /opt/DOC

mkdir /opt/DOC/gravitee

cd /opt/DOC/gravitee

mkdir -p config

curl -L -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/docker-compose.yml

curl -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/.env

cd config && { curl -O https://raw.githubusercontent.com/gravitee-io/graviteeio-access-management/2.x/docker/compose/config/nginx.conf ; cd -; }

docker-compose pull

### Zmień w docker-compose.yml

- MGMT_API_URL=http://Adress IP:${NGINX_PORT}/am
- MGMT_UI_URL=http://Adres IP:${NGINX_PORT}/am/ui


docker-compose up

