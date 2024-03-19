# Instrucciones para compilar en "linux" "arm"

```sh
mkdir workspace
docker run --rm -it -v ${PWD}/workspace:/workspace golang:1.22-alpine /bin/sh
```

Dentro de docker
```sh
apk add --update --no-cache bash ca-certificates curl git
cd /workspace
git clone https://github.com/fclairamb/ftpserver.git .
CGO_ENABLED=0 GOOS=linux GOARCH=arm  go build -mod=readonly -ldflags='-w -s' -v -o ftpserver
```

Ya disponemos de `ftpserver` compilado para GOOS=linux GOARCH=arm en:
```sh
./workspace/ftpserver
```