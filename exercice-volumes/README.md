# Nginx

Image Windows Core Server avec Nginx installé.

# Remarque

la version de nginx pour Windows est considérée comme une version bêta.

# Exécuter Nginx

Exécutez docker image build pour exécuter les étapes dans le Dockerfile :

```
docker image build -t <DockerId>/nginx:1.0 .
```

Créez un conteneur qui utilise la nouvelle image que vous venez de créer :

```
docker container run -d -p 80:80 --name nginx <DockerId>/nginx:1.0
```

Affichez l'adresse IP du conteneur :

```
docker inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' nginx
```
