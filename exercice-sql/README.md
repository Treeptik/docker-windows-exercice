# 

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile :
```
docker image build -t antony13100/nerd-dinner-db .
docker image build -t antony13100/nerd-dinner-web .
```

Créez un conteneur qui utilise la nouvelle image que vous venez de créer :

```
docker container run -d -p 1433:1433 --name nerd-dinner-db antony13100/nerd-dinner-db
docker container run -d -p 8081:80 --name nerd-dinner-web antony13100/nerd-dinner-web
```
