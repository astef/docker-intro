## Что такое Docker Engine?
Это клиент-серверное приложение:                                <!-- .element: class="fragment" -->
- сервер: демон/служба, команда *`dockerd`*                     <!-- .element: class="fragment" -->
- REST API, реализуется сервером                                <!-- .element: class="fragment" -->
- клиент (CLI): *`docker`*                                      <!-- .element: class="fragment" -->

+++
### Запуск dockerd
- будет запущен сразу после установки         <!-- .element: class="fragment" -->
- запускается при старте системы              <!-- .element: class="fragment" -->
  - Windows: служба Docker                    <!-- .element: class="fragment" -->
  - Ubuntu: systemd (15+), upstart (14.04)    <!-- .element: class="fragment" -->
- конфигурируется с помощью daemon.json       <!-- .element: class="fragment" -->
- пишет логи:


+++
### Функционал dockerd
- Создаёт и управляет объектами:              <!-- .element: class="fragment" -->
  - `images`                                  <!-- .element: class="fragment" -->
  - `containers`                              <!-- .element: class="fragment" -->
  - `networks`                                <!-- .element: class="fragment" -->
  - `volumes`                                 <!-- .element: class="fragment" -->
- Вызывает внешние системы:                   <!-- .element: class="fragment" -->
  - переходит в режим роя (`swarm mode`), чтобы масштабировать контейнеры, объединённые в сервисы (`services`) между разными демонами<!-- .element: class="fragment" -->
  - ищет образы (`images`) во внешних реестрах (`registry`). Реестр по умолчанию - http://hub.docker.com<!-- .element: class="fragment" -->
