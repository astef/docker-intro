## Контейнеры
- можно запускать на основе образов: `docker run`
- приостанавливать/возобновлять: `docker pause`, `docker unpause`
- подключаться: `docker attach`
- выполнять команду внутри: `docker exec`
+++
### Побочные эффекты
- сети, через выставленные порты
- подключённые тома
+++
### Возможности
- Логи `docker logs`, 9 драйверов, в т.ч.:
  - json-file
  - syslog
  - journald
  - gelf (Graylog/Logstash compatible)
  - etwlogs (Event Tracing for Windows)
- Мониторинг `docker stats`
- Политики перезапуска `docker run --restart always`
- Ограничение ресурсов (cpu/mem/swap)