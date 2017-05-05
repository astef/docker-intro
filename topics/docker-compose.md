## Docker Compose
Простой способ определять мультиконтейнерные приложения.

Типичный пример использования:
```shell
$ docker-compose up -d
$ ./run_tests
$ docker-compose down
```
+++
### docker-compose.yml
```yaml
version: '3'
services:
  rubik:
    image: srv10-proget.spb.helix.ru/hub/rubikserver:latest
    ports:
      - "5556:80"
    depends_on:
      - pg
      - rmq
      - store-migrator
    environment:
      - ASPNETCORE_URLS=http://*:80
      - "FhirStoreOptions:ConnectionString=server=pg;user id=postgres;password=postgres;database=fhirdb; Persist Security Info=true"
      - "QueueOptions:HostName=rmq"
      - "QueueOptions:Port=5672"
      - "QueueOptions:UserName=guest"
      - "QueueOptions:Password=guest"
    networks:
      main:
        aliases:
          - rubik
  pg:
    image: postgres:9.5.6
    ports:
      - "5432:5432"
    environment:
      - POSTGRES_PASSWORD=postgres
    networks:
      main:
        aliases:
          - pg
  rmq:
    image: rabbitmq:3-management
    ports:
      - "15672:15672"
    networks:
      main:
        aliases:
          - rmq
  store-migrator:
    image: srv10-proget.spb.helix.ru/hub/rubik-store-migrator:latest
    depends_on:
      - pg
    environment:
      - "ConnectionString=server=pg;user id=postgres;password=postgres;database=postgres; Persist Security Info=true"
      - DBName=fhirdb
    networks:
      main:
  notifier:
    image: srv10-proget.spb.helix.ru/hub/rubik-notifier:latest
    depends_on:
      - rubik
    environment:
      - "FhirSubscriptionOptions:HostName=http://rubik"
      - "FhirSubscriptionOptions:FhirBase=/fhir"
      - "FhirSubscriptionOptions:AuthBase=/auth"
      - "NotifierOptions:HostName=rmq"
      - "NotifierOptions:UserName=guest"
      - "NotifierOptions:Password=guest"
      - "FhirMetadataUrl=http://rubik/fhir/metadata"
    networks:
      main:
networks:
  main:    
```
+++


