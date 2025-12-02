# Docker

## 🐳 Docker Installation

### **Windows**

-   Docker Desktop installieren\
-   WSL2 aktivieren (empfohlen)

### **Ubuntu / Debian**

``` bash
sudo apt update
sudo apt install ca-certificates curl gnupg
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu   $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

## 🐳 Container verwalten

-   **Container starten:** `docker run <image>`
-   **Interaktiv starten:** `docker run -it <image> /bin/bash`
-   **Im Hintergrund:** `docker run -d <image>`
-   **Laufende Container:** `docker ps`
-   **Alle Container:** `docker ps -a`
-   **Container stoppen:** `docker stop <id>`
-   **Container löschen:** `docker rm <id>`
-   **Logs anzeigen:** `docker logs <id>`
-   **In laufenden Container einsteigen:** `docker exec -it <id> bash`

## 📦 Images verwalten

-   **Images anzeigen:** `docker images`
-   **Image herunterladen:** `docker pull <image>`
-   **Image löschen:** `docker rmi <image>`
-   **Image bauen:** `docker build -t name:tag .`

## 📂 Volumes & Daten

-   **Volumes anzeigen:** `docker volume ls`
-   **Volume erstellen:** `docker volume create <name>`
-   **Volume löschen:** `docker volume rm <name>`
-   **Volume mounten:** `docker run -v <volume>:/path <image>`

## 🌐 Netzwerk

-   **Netzwerke anzeigen:** `docker network ls`
-   **Netzwerk erstellen:** `docker network create <name>`
-   **Container verbinden:** `docker network connect <net> <container>`

## 🧹 System aufräumen

-   **Ungenutztes entfernen:** `docker system prune`
-   **Alles entfernen:** `docker system prune -a`

## 📄 Docker Compose

### 📄 Definition: Docker Compose

**Docker Compose** ist ein Tool, mit dem man mehrere Container über eine
einzige Datei (`docker-compose.yml`) definieren, starten und verwalten
kann.

***Vorteile***

-   Mehrere Dienste (z. B. App + DB + Cache) in einer Datei
-   Einfaches Starten: `docker compose up -d`
-   Versionierbar (Git)
-   Automatische Netzwerke zwischen Containern

-   **Starten:** `docker compose up`
-   **Mit Neubauen:** `docker compose up --build`
-   **Im Hintergrund:** `docker compose up -d`
-   **Stoppen:** `docker compose down`
-   **Dienste anzeigen:** `docker compose ps`


??? tip

    ✔️ Container automatisch neustarten
    ``` yaml
    restart: unless-stopped
    ```

    ✔️ Logs live ansehen
    ``` bash
    docker compose logs -f
    ````

    ✔️ Alte Ressourcen löschen
    ``` bash
    docker system prune -a
    ```

    ✔️ CLI Autocomplete aktivieren
    ``` bash
    sudo apt install bash-completion
    ```

    ✔️ Healthchecks verwenden
    ``` yaml
    healthcheck:
    test: ["CMD", "curl", "-f", "http://localhost:5678"]
    interval: 30s
    timeout: 10s
    retries: 5
    ```

    ✔️ Updates von Images ziehen
    ``` bash
    docker pull n8nio/n8n
    docker compose up -d
    ```