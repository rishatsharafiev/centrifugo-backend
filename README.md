# centrifugo-backend

# TODO
[X] подключить мониторинг
[X] добавить дашбоард для centrifugo
[ ] настройка различных окружений 
[ ] проверить конфиг nginx на тесте
[ ] metalmatze/alertmanager-bot
[ ] docker-swarm

# Настройки
### Конфиг centrifugo
Скопировать конфиг
```
cp centrifugo/config.json-example centrifugo/config.json
```
добавить секреты


### Конфиг nginx
https://centrifugal.github.io/centrifugo/deploy/nginx/

# Мониторинг
https://centrifugal.github.io/centrifugo/deploy/monitoring/

Добавить в centrifugo/config.json
```
"prometheus": true
```
Забирать данные с /metrics


# TLS
https://centrifugal.github.io/centrifugo/deploy/tls/

Добавить в centrifugo/config.json
```
"tls_autocert": true,
"tls_autocert_host_whitelist": "www.example.com",
"tls_autocert_cache_dir": "/tmp/certs",
"tls_autocert_email": "user@example.com",
"tls_autocert_http": true,
"tls_autocert_http_addr": ":80"
```

# Тюнинг ОС
### Лимиты на открытые сокеты файлов
```
ulimit -n # Ограничиваем максимальное часло открытых файлов. 65536 в хост системе
```

### Много сокетов в TIME_WAIT
https://centrifugal.github.io/centrifugo/deploy/tuning/#lots-of-sockets-in-time_wait-state

# Supervisor
- Скопировать содержимое папки supervisor в /etc/supervisor
- Перезапустить sudo systemctl start supervisord.service