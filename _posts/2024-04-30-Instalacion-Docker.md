---
title: Instalación Docker 
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

# Instalación de Docker
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

Una vez ya está instalado Docker instalamos la aplicación:
```
docker run --name some-mariadb -d -e MYSQL_ROOT_PASSWORD=hellodocker -e MYSQL_DATABASE=easyappointments mariadb:latest
docker run --name some-easyappointments -d --link some-mariadb:db -p 8888:8888 jamrizzi/easyappointments:latest
```

Usage
Environment Variable	Deafult Value
BASE_URL	"http://localhost:8888"
LANGUAGE	"english"
DEBUG	false
DB_HOST	"db"
DB_NAME	"easyappointments"
DB_USERNAME	"root"
DB_PASSWORD	"hellodocker"
GOOGLE_SYNC_FEATURE	false
GOOGLE_PRODUCT_NAME	
GOOGLE_CLIENT_ID	
GOOGLE_CLIENT_SECRET	
GOOGLE_API_KEY	
TZ	"UTC"





