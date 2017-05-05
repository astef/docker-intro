## Образы
  - строить: `docker build`
  - получать: `docker pull`
  - отправлять: `docker push`
+++
### Образы иммутабельны
![Images](/assets/image/docker_images.png)
+++
### Dockerfile
Инструкция по сборке образа для команды `docker build`
```Dockerfile
FROM komljen/ubuntu
MAINTAINER Alen Komljen <alen.komljen@live.com>

ENV PG_VERSION 9.3
ENV USER docker
ENV PASS SiHRDZ3Tt13uVVyH0ZST

RUN \
  echo "deb http://apt.postgresql.org/pub/repos/apt/ trusty-pgdg main" \
       > /etc/apt/sources.list.d/pgdg.list && \
  curl -sL https://www.postgresql.org/media/keys/ACCC4CF8.asc \
       | apt-key add - && \
  apt-get update && \
  apt-get -y install \
          postgresql-${PG_VERSION} \
          postgresql-contrib-${PG_VERSION} && \
  rm -rf /var/lib/apt/lists/*

COPY start.sh start.sh

RUN rm /usr/sbin/policy-rc.d
CMD ["/start.sh"]

EXPOSE 5432
```
+++
### ENTRYPOINT
* Каждый контейнер - обычная программа с вводом и выводом
* `ENTRYPOINT` - точка входа
* `ENTRYPOINT` по умолчанию `/bin/sh -c`
+++
### Управление образами
- Docker Hub<!-- .element: class="fragment" -->
  - реестр по умолчанию<!-- .element: class="fragment" -->
  - `docker pull nginx`<!-- .element: class="fragment" -->
- Много решений для приватных реестров<!-- .element: class="fragment" -->
  - по умолчанию требуется https (будет ошибка)<!-- .element: class="fragment" -->
  - пример ProGet:<!-- .element: class="fragment" -->https://srv10-proget.spb.helix.ru/<!-- .element: class="fragment" -->
```shell
docker login -u Admin -p Admin srv10-proget.spb.helix.ru/docker
docker tag myImage srv10-proget.spb.helix.ru/docker/hub/myImage
docker push srv10-proget.spb.helix.ru/docker/hub/myImage
```

