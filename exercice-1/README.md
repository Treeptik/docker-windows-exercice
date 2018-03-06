# Construire une image de site web simple

Jetez un oeil � Dockerfile pour cette application, qui cr�e un simple site Web ASP.NET en cours d'ex�cution qui affiche le nom d'h�te du serveur. Il n'y a que deux instructions:
	
	* [FROM](https://docs.docker.com/engine/reference/builder/#from) - Sp�cifie l'image � utiliser comme point de d�part pour cette image. 
																	   Microsoft / aspnet est une image d�tenue par Microsoft, qui vient avec IIS et ASP.NET install� sur Windows Server Core
    * [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie un fichier de l'h�te dans l'image, � un emplacement connu.

Ex�cutez **docker image build** pour ex�cuter les �tapes dans le Dockerfile: 
```
docker image build -t <dockerId>/hostname-app .
```
```
docker container run -d -p 80:80 --name app <dockerId>/hostname-app
```
r�cup�rer l'adresse IP du conteneur:
```
docker container inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' app
```
vous pouvez ouvrir votre navigateur avec l'adresse IP du conteneur et voir le site ASP.NET:

## Poussez vos images sur Docker Hub

```
docker image push <dockerId>/hostname-app
```
