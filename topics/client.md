## Клиент docker
![Docker Client](assets/image/DockerClient.png)

+++
### Попробуем команды
- `docker --help`: получить список доступных команд
- `docker ps`, `docker ps --help`, `docker ps -a`
- `-H dev10-tcagent`
- `docker run hello-world`
+++
### Попробуем API
- развернём `rocketbuildrapid/rapid`  
```shell
sudo docker run -d -p 35200:8080 \
  -v /var/run/docker.sock:/var/run/docker.sock \
  ozlerhakan/rapid
```
+++
### Попробуем Portainer
```shell
docker run -d -p 9000:9000 \
  --privileged \
  -v /var/run/docker.sock:/var/run/docker.sock \
  portainer/portainer
```
