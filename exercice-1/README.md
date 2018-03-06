# Construire une image de site web simple

Jetez un oeil à Dockerfile pour cette application, qui crée un simple site Web ASP.NET en cours d'exécution qui affiche le nom d'hôte du serveur. Il n'y a que deux instructions:
	
	* [FROM](https://docs.docker.com/engine/reference/builder/#from) - Spécifie l'image à utiliser comme point de départ pour cette image. 
																	   Microsoft / aspnet est une image détenue par Microsoft, qui vient avec IIS et ASP.NET installé sur Windows Server Core
    * [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie un fichier de l'hôte dans l'image, à un emplacement connu.

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
