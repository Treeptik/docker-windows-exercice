# 

Ex�cutez **docker image build** pour ex�cuter les �tapes dans le Dockerfile :
```
docker image build -t <DockerId>/nerd-dinner-db .
```
```
docker image build -t <DockerId>/nerd-dinner-web .
```

Cr�ez un conteneur qui utilise la nouvelle image que vous venez de cr�er :

```
docker container run -d -p 1433:1433 --name nerd-dinner-db <DockerId>/nerd-dinner-db
```
```
docker container run -d -p 8081:80 --name nerd-dinner-web <DockerId>/nerd-dinner-web
```
