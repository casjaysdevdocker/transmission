## 👋 Welcome to transmission 🚀  

Transmission is designed for easy, powerful use. Transmission has the features you want from a BitTorrent client:  
encryption, a web interface, peer exchange, magnet links, DHT, µTP, UPnP and NAT-PMP port forwarding, webseed support,  
watch directories, tracker editing, global and per-torrent speed limits, and more.  
  
  
## Install my system scripts  

```shell
 sudo bash -c "$(curl -q -LSsf "https://github.com/systemmgr/installer/raw/main/install.sh")"
 sudo systemmgr --config && sudo systemmgr install scripts  
```
  
## Automatic install/update  
  
```shell
dockermgr update transmission
```
  
## Install and run container
  
```shell
mkdir -p "$HOME/.local/share/srv/docker/transmission/volumes"
git clone "https://github.com/dockermgr/transmission" "$HOME/.local/share/CasjaysDev/dockermgr/transmission"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/transmission/rootfs/." "$HOME/.local/share/srv/docker/transmission/volumes/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-transmission \
--hostname transmission \
-e TZ=${TIMEZONE:-America/New_York} \
-v /mnt/downloads:/data/downloads:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-transmission/volumes/data:/data:z \
-v $HOME/.local/share/srv/docker/casjaysdevdocker-transmission/volumes/config:/config:z \
-p 0.0.0.0:9091:9091 \
-p 0.0.0.0:51413:51413 \
-p 0.0.0.0:51413:51413/udp \
casjaysdevdocker/transmission:latest
```
  
## via docker-compose  
  
```yaml
version: "2"
services:
  ProjectName:
    image: casjaysdevdocker/transmission
    container_name: casjaysdevdocker-transmission
    environment:
      - TZ=America/New_York
      - HOSTNAME=transmission
    volumes:
      - /mnt/downloads:/data/downloads:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-transmission/volumes/data:/data:z
      - $HOME/.local/share/srv/docker/casjaysdevdocker-transmission/volumes/config:/config:z
    ports:
      - 0.0.0.0:9091:9091
      - 0.0.0.0:51413:51413
      - 0.0.0.0:51413:51413/udp
    restart: always
```
  
## Get source files  
  
```shell
dockermgr download src casjaysdevdocker/transmission
```
  
OR
  
```shell
git clone "https://github.com/casjaysdevdocker/transmission" "$HOME/Projects/github/casjaysdevdocker/transmission"
```
  
## Build container  
  
```shell
cd "$HOME/Projects/github/casjaysdevdocker/transmission"
buildx 
```
  
## Authors  
  
🤖 casjay: [Github](https://github.com/casjay) 🤖  
⛵ casjaysdevdocker: [Github](https://github.com/casjaysdevdocker) [Docker](https://hub.docker.com/u/casjaysdevdocker) ⛵  
