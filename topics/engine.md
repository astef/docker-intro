## Что такое Docker Engine?
Docker Engine - это клиент-серверное приложение:
- сервер: демон/служба, запущенная командой `dockerd` <!-- .element: class="fragment" -->
- REST API, который определяет интерфейс, реализуемый сервером <!-- .element: class="fragment" -->
- клиент, который пользоваться сервером через командную строку: `docker` <!-- .element: class="fragment" -->

+++
### Запуск dockerd
- будет запущен сразу после установки<!-- .element: class="fragment" -->
- запускается при старте системы
  - Windows: служба Docker
  - Ubuntu: systemd (15+), upstart (14.04)<!-- .element: class="fragment" -->
- конфигурируется с помощью daemon.json<!-- .element: class="fragment" -->
- пишет логи:
  - Windows:
  - Linux:<!-- .element: class="fragment" -->

+++
### Функционал dockerd
- Создаёт и управляет объектами:
  - `images`
  - `containers`<!-- .element: class="fragment" -->
  - `networks`<!-- .element: class="fragment" -->
  - `volumes`<!-- .element: class="fragment" -->
- Вызывает внешние системы:<!-- .element: class="fragment" -->
  - переходит в режим роя (`swarm mode`), чтобы масштабировать контейнеры, объединённые в сервисы (`services`) между разными демонами<!-- .element: class="fragment" -->
  - ищет образы (`images`) во внешних реестрах (`registry`). Реестр по умолчанию - http://hub.docker.com
