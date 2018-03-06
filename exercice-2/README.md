# Créez et exécutez une image de site Web plus complexe

Pour l'exemple suivant, le Dockerfile est une meilleure représentation d'un script du monde réel. 

Ce sont les principales caractéristiques:
	
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - L'image de base est microsoft/iis:windowsservercore, donc l'image va démarrer avec un déploiement Windows Server 2016 propre, avec IIS déjà installé.
* [SHELL](https://docs.docker.com/engine/reference/builder/#shell) - Utilisation de l'instruction SHELL pour basculer vers PowerShell lors de la création du Dockerfile, donc les commandes à exécuter sont toutes dans PowerShell.
* Configuration d'IIS pour écrire toutes les sorties de journal dans un seul fichier, à l'aide de la cmdlet Set-WebConfigurationProperty.
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie du script de démarrage start.ps1 et les fichiers index.html de l'hôte dans l'image.
* [SHELL](https://docs.docker.com/engine/reference/builder/#entrypoint) - Il spécifie start.ps1 comme ENTRYPOINT à exécuter lorsque les conteneurs démarrent. Le script démarre le service Windows IIS et relaie les entrées du fichier journal à la console
* [HEALTHCHECK](https://docs.docker.com/engine/reference/builder/#healthcheck) - L'ajoute un HEALTHCHECK qui envoie une requête HTTP GET au site et renvoie s'il a obtenu un code de réponse 200
