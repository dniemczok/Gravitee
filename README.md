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

docker-compose up
