# Nginx

Image Windows Core Server avec Nginx install�.

# Remarque

la version de nginx pour Windows est consid�r�e comme une version b�ta.

# Ex�cuter Nginx

Ex�cutez docker image build pour ex�cuter les �tapes dans le Dockerfile :

```
docker image build -t <DockerId>/nginx:1.0 .
```

Cr�ez un conteneur qui utilise la nouvelle image que vous venez de cr�er :

```
docker container run -d -p 80:80 --name nginx <DockerId>/nginx:1.0
```

Affichez l'adresse IP du conteneur :

```
docker inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' nginx
```
