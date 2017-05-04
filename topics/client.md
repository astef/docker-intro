## Клиент docker
![Docker Client](assets/DockerClient.png)

+++
## Попробуем команды
- `docker --help`: получить список доступных команд
- `docker ps`, `docker ps --help`, `docker ps -a`
- `-H dev10-tcagent`
- `docker run hello-world`
+++
### Попробуем API
- развернём `rocketbuildrapid/rapid`
  <!-- .element: class="fragment" -->
```shell
sudo docker run -d -p 35200:8080 -v /var/run/docker.sock:/var/run/docker.sock ozlerhakan/rapid
```
  <!-- .element: class="fragment" -->
  - asd
http://dev10-tcagent03:32769/
### Попробуем Portainer

