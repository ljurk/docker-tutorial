# Docker Tutorial
1. Docker Installation ([Quelle](https://docs.docker.com/engine/install/debian/))

```
sudo apt-get update && sudo apt-get install curl
curl bash -c "$(curl https://raw.githubusercontent.com/ljurk/docker-tutorial/master/install.sh)"
```

2. starten eines containers mit dem `docker` Kommando

Syntax: `docker run <IMAGE>`

Beispiele:
- `docker run hello-world`
- `docker run -it debian /bin/bash` (interactive, tty, image, command)
- `docker run -d -p 80:80 -v "$PWD"/html:/usr/share/nginx/html:ro nginx`(deatached, port, volume, image)

3. starten mehrerer Container mit docker-compose

```
curl -O https://raw.githubusercontent.com/ljurk/docker-tutorial/master/docker-compose.yml
docker-compose up
```

Testen des Reverse Proxies: `curl -H "Host: whoami.local" localhost`

4. andere nützliche Befehle

- Auflistung aller laufenden Container: `docker ps`
- Logs eines Containers einsehen: `docker logs <ID oder NAME>`
- Stoppen eines Containers: `docker stop <ID oder NAME>`
    - der Container könnte dannach ohne Datenverlust neugestartet werden: `docker start <ID oder NAME>`
- Löschen eines Containers: `docker rm <ID oder NAME>`

5. Docker Images
- werden vom Entwickler bereitgestellt und enthalten alle Pakete und Konfigurationen die für den Betrieb der Anwendung nötig sind
- das `Dockerfile` definiert wie dieses Image aussieht
- real-world-Beispiel
```
FROM python:3.7-alpine

WORKDIR /opt/links
EXPOSE 5000

#copy requirements first, so that the package installation will be cached
COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

#copy all files to workdir
COPY . .

CMD ["python", "main.py"]
```

- simples Beispiel:
```
FROM debian

CMD echo "Hello world"
```
- Erstellung des Images: `docker build . -t <NAME DES IMAGES>`

vi: spelllang=de_de
