## 👋 Welcome to transmission 🚀  

transmission README  
  
  
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
dockerHome="/var/lib/srv/$USER/docker/casjaysdevdocker/transmission/transmission/latest/rootfs"
mkdir -p "/var/lib/srv/$USER/docker/transmission/rootfs"
git clone "https://github.com/dockermgr/transmission" "$HOME/.local/share/CasjaysDev/dockermgr/transmission"
cp -Rfva "$HOME/.local/share/CasjaysDev/dockermgr/transmission/rootfs/." "$dockerHome/"
docker run -d \
--restart always \
--privileged \
--name casjaysdevdocker-transmission-latest \
--hostname transmission \
-e TZ=${TIMEZONE:-America/New_York} \
-v "$dockerHome/data:/data:z" \
-v "$dockerHome/config:/config:z" \
-p 80:80 \
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
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/transmission/transmission/latest/rootfs/data:/data:z"
      - "/var/lib/srv/$USER/docker/casjaysdevdocker/transmission/transmission/latest/rootfs/config:/config:z"
    ports:
      - 80:80
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
