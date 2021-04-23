# vi: spelllang=de_de
2. Docker Installation

```
apt-get update && apt-get install apt-transport-https ca-certificates curl gnupg lsb-release
curl -fsSL https://download.docker.com/linux/debian/gpg | gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/debian $(lsb_release -cs) stable" | tee /etc/apt/sources.list.d/docker.list > /dev/null
apt-get update && apt-get install docker-ce docker-ce-cli containerd.io
```

3. starten eines containers mit dem `docker` Kommando

`docker run -it debian /bin/bash`

1. starten mehrerer Container mit docker-compose

```
curl -O https://github.com/ljurk/docker-tutorial/docker-compose.yml
docker-compose up
```

2. volumen, ports, environment variablen, reverse proxy
