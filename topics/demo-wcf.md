## Контейнеризуем WCF сервис

```Dockerfile
FROM microsoft/wcf
RUN mkdir C:\WcfService
RUN powershell -NoProfile -Command \
    Import-module IISAdministration; \
    New-IISSite -Name "WcfService" -PhysicalPath C:\WcfService -BindingInformation "*:83:"
EXPOSE 83
ADD content/ /WcfService
```

```shell
docker build -t crm-wcf
docker run -d -p 83:83 \
    --name crm crm-wcf
```

+++
### Простой мониторинг ресурсов контейнера

```shell
docker run --rm -it \
    --name ctop
    -e DOCKER_HOST=tcp://dev10-srv16:2375
    -v //var/run/docker.sock:/var/run/docker.sock
    quay.io/vektorlab/ctop
```
