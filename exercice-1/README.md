# Construire une image de site web simple

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t <dockerId>/hostname-app .
```
```
docker container run -d -p 80:80 --name app <dockerId>/hostname-app
```
récupérer l'adresse IP du conteneur:
```
docker container inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' app
```
vous pouvez ouvrir votre navigateur avec l'adresse IP du conteneur et voir le site ASP.NET:

## Poussez vos images sur Docker Hub

```
docker image push <dockerId>/hostname-app
```