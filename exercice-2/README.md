# Cr�ez et ex�cutez une image de site Web plus complexe

Pour l'exemple suivant, le Dockerfile est une meilleure repr�sentation d'un script du monde r�el. 

Ce sont les principales caract�ristiques:
	
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - L'image de base est microsoft/iis:windowsservercore, donc l'image va d�marrer avec un d�ploiement Windows Server 2016 propre, avec IIS d�j� install�.
* [SHELL](https://docs.docker.com/engine/reference/builder/#shell) - Utilisation de l'instruction SHELL pour basculer vers PowerShell lors de la cr�ation du Dockerfile, donc les commandes � ex�cuter sont toutes dans PowerShell.
* Configuration d'IIS pour �crire toutes les sorties de journal dans un seul fichier, � l'aide de la cmdlet Set-WebConfigurationProperty.
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie du script de d�marrage start.ps1 et les fichiers index.html de l'h�te dans l'image.
* [SHELL](https://docs.docker.com/engine/reference/builder/#entrypoint) - Il sp�cifie start.ps1 comme ENTRYPOINT � ex�cuter lorsque les conteneurs d�marrent. Le script d�marre le service Windows IIS et relaie les entr�es du fichier journal � la console
* [HEALTHCHECK](https://docs.docker.com/engine/reference/builder/#healthcheck) - L'ajoute un HEALTHCHECK qui envoie une requ�te HTTP GET au site et renvoie s'il a obtenu un code de r�ponse 200
