---
title: Instalacion Docker 
description: Examples of text, typography, math equations, diagrams, flowcharts, pictures, videos, and more.
author: Luis
date: 2024-05-23 12:00:00 +0800
categories: [Blogging, Demo]
tags: [typography]
pin: true
math: true
mermaid: true
image:
  path: /commons/devices-mockup.png
  lqip: data:image/webp;base64,UklGRpoAAABXRUJQVlA4WAoAAAAQAAAADwAABwAAQUxQSDIAAAARL0AmbZurmr57yyIiqE8oiG0bejIYEQTgqiDA9vqnsUSI6H+oAERp2HZ65qP/VIAWAFZQOCBCAAAA8AEAnQEqEAAIAAVAfCWkAALp8sF8rgRgAP7o9FDvMCkMde9PK7euH5M1m6VWoDXf2FkP3BqV0ZYbO6NA/VFIAAAA
  alt: Responsive rendering of Chirpy theme on multiple devices.
---

# Instalacion de Docker y Docker Compose
Set up Docker's apt repository.

```
# Add Docker's official GPG key:
sudo apt-get update
sudo apt-get install ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc

# Add the repository to Apt sources:
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
```

To install the latest version, run:

```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

```

Verify that the Docker Engine installation is successful by running the hello-world image.
```
sudo docker run hello-world
```

Una vez ya esta instalado Docker vamos apreparar el archivo con nuestra necesidades:
Se pueden realizar diferentes cambiaos, como por ejemplo puertos y demas, pero el que si que si hay que cambiar es - SITE_URL
```
vi docker-compose.ym
```
```
version: '2'

services:
  freescout-app:
    image: tiredofit/freescout
    container_name: freescout-app
    ports:
    - 80:80
    links:
    - freescout-db
    volumes:
    ### If you want to perform customizations to the source and have access to it, then uncomment this line - This includes modules
    #- ./data:/www/html
    ### Or, if you just want to use Stock Freescout and hold onto persistent files like cache and session use this, one or the other.
    - ./data:/data
    ### If you want to just keep the original source and add additional modules uncomment this line
    #- ./modules:/www/html/Modules
    - ./logs/:/www/logs
    environment:
    - CONTAINER_NAME=freescout-app
    
    - DB_HOST=freescout-db
    - DB_NAME=freescout
    - DB_USER=freescout
    - DB_PASS=freescout

    - SITE_URL=http://<<Ponemos la IP de nuestro ordenador>>
    - ADMIN_EMAIL=admin@admin.com
    - ADMIN_PASS=freescout
    - ENABLE_SSL_PROXY=FALSE
    - DISPLAY_ERRORS=FALSE
    - TIMEZONE=America/Vancouver
    restart: always

  freescout-db:
    image: tiredofit/mariadb
    container_name: freescout-db
    volumes:
      - ./db:/var/lib/mysql
    environment:
      - ROOT_PASS=password
      - DB_NAME=freescout
      - DB_USER=freescout
      - DB_PASS=freescout

      - CONTAINER_NAME=freescout-db
    restart: always

  freescout-db-backup:
    container_name: freescout-db-backup
    image: tiredofit/db-backup
    links:
     - freescout-db
    volumes:
      - ./dbbackup:/backup
    environment:
      - CONTAINER_NAME=freescout-db-backup
      - DB_HOST=freescout-db
      - DB_TYPE=mariadb
      - DB_NAME=freescout
      - DB_USER=freescout
      - DB_PASS=freescout
      - DB01_BACKUP_INTERVAL=1440
      - DB01_BACKUP_BEGIN=0000
      - DB_CLEANUP_TIME=8640
      - COMPRESSION=BZ
      - MD5=TRUE
    restart: always
```

Creamos los contenedores:
```
docker compose up -d
```

Y ya solo queda probar nuestro servidor:
http://<<nuestra IP>>
