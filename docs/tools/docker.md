# Docker

**Schlagwörter:** [Docker Compose](#Docker-compose.yml),[Installation](#Installation-für-Linux)

## Ansichten und Infos
|Docker-Befehl|Erklärung|
|---|---|
|docker --help|Hilfe für die Docker -CLI anzeigen|
|docker --version|Die VErsion der Docker Installation anzeigen|
|docker info|Systemweite Informaitonen über die Docker-Installation anzeigen|
|docker ps|Laufende Container auflisten|
|docker ps -a|alle Container auflisten|

Installation Docker-Compose

hub.docker.com

## Installation für Linux

```bash
apt install curl

curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh ./get-docker.sh

# gibt dem aktuellen User Rechte um nicht immer sudo eingeben zu müssen
sudo usermod -aG docker $USER



#Port 80 der Netzwerkkarte wird an Port 80 des Conatiner weitergeleitet
docker run -p 80:80 (NAme des PRogramm)

docker stop (Containername) oder STRG+C

```

## Docker-compose.yml

|Docker-Befehl|Erklärung|
|---|---|
nano docker-compose.yml|# legt die docker-compose.yml Datei an, # schließen der Datei STRG+O , y ,  STRG+X|
|docker compose up -d| starten der Datei, -d=detached gibt den Cursor der Kommandozeile frei

## Updates

docker compose pull 

oder

Eintrag in der docker-compose.yml

watchtower:
  image: container/watchtower
