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
### Мониторим ресурсы контейнера

```shell
docker stats --all
```
