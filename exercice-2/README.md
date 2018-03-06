# Créez et exécutez une image de site Web plus complexe

Pour l'exemple suivant, le Dockerfile est une meilleure représentation d'un script du monde réel. 

Ce sont les principales caractéristiques:
	
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - L'image de base est ```microsoft/iis:windowsservercore```, donc l'image va démarrer avec un déploiement Windows Server 2016 propre, avec IIS déjà installé.
* [SHELL](https://docs.docker.com/engine/reference/builder/#shell) - Utilisation de l'instruction SHELL pour basculer vers PowerShell lors de la création du Dockerfile, donc les commandes à exécuter sont toutes dans PowerShell.
* Configuration d'IIS pour écrire toutes les sorties de journal dans un seul fichier, à l'aide de la commande ```Set-WebConfigurationProperty```.
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie du script de démarrage start.ps1 et les fichiers index.html de l'hôte dans l'image.
* [SHELL](https://docs.docker.com/engine/reference/builder/#entrypoint) - Spécifie ```start.ps1``` comme ```ENTRYPOINT``` à exécuter lorsque les conteneurs démarrent. Le script démarre le service Windows IIS et relaie les entrées du fichier journal à la console.
* [HEALTHCHECK](https://docs.docker.com/engine/reference/builder/#healthcheck) - Ajout d'un HEALTHCHECK qui envoie une requête ```HTTP GET``` au site et renvoie s'il a obtenu un code de réponse 200.

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t <dockerId>/tweet-app .
```
```
docker container run -d -p 8080:80 --name tweet-app <dockerId>/tweet-app
```
récupérer l'adresse IP du conteneur:
```
docker container inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' tweet-app
```
vous pouvez ouvrir votre navigateur avec l'adresse IP du conteneur et voir le site :

## Poussez vos images sur Docker Hub

```
docker image push <dockerId>/tweet-app
```