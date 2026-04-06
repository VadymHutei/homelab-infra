# Homelab Infra
Репозиторій для збереження різних інфраструктурних файлів і налаштувань. А саме:
- reverse proxy
  - налаштування nginx
  - Dockerfile
  - compose.yaml

## Налаштування firewall на сервері
вимикаємо IPv6 в конфігу ufw
/etc/default//ufw - міняємо IPV6=yes на IPV6=no

додаємо правила ufw
``` shell
sudo ufw allow 80/tcp
```
```shell
sudo ufw allow 443/tcp
```
відкриваємо 22 порт для SSH доступу тільки в локальній мережі
```shell
sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp
```
вмикаємо ufw
```shell
sudo ufw enable
```

## Створення мереж Docker
```shell
docker network create -d bridge proxy
docker network create -d bridge backend
```
