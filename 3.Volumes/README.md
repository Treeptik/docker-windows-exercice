# Persistance de données

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile :
```
docker image build -t <DockerId>/myiis .
```

Créez un conteneur qui utilise la nouvelle image que vous venez de créer :

```
docker container run -d -p 80:80 --name myiis <DockerId>/myiis
```

Affichez l'adresse IP du conteneur :

```
docker inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' myiis
```
