# int-34-monitoring
## Что делаем?

1. Запускаем Blackbox Exporter: __./blackbox_exporter --config.file=blackbox.yml &__
2. Запускаем Prometheus: __./prometheus --config.file=prometheus.yml &__

## Как проверим?

В браузере переходим по адресу: http://localhost:9090 и в разделе "Status" > "Targets" смотрим, что job blackbox отображается в списке и его статус "UP".

Для запроса метрик выполним команду: __curl http://localhost:9090/api/v1/query?query=probe_success__
Если сайт https://ptsecurity.com доступен, то получим ответ, содержащий метрику probe_success со значением 1 в "value". Если сайт недоступен, значение будет 0.

