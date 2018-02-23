# Persistance de donn�es

Ex�cutez **docker image build** pour ex�cuter les �tapes dans le Dockerfile :
```
docker image build -t <DockerId>/myiis .
```

Cr�ez un conteneur qui utilise la nouvelle image que vous venez de cr�er :

```
docker container run -d -p 80:80 --name myiis <DockerId>/myiis
```

Affichez l'adresse IP du conteneur :

```
docker inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' myiis
```
