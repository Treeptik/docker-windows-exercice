# Créez et exécutez une image de site Web plus complexe

Pour l'exemple suivant, le Dockerfile est une meilleure représentation d'un script du monde réel. 

Ce sont les principales caractéristiques:
	
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - Spécifie l'image à utiliser comme point de départ pour cette image. 
Microsoft / aspnet est une image détenue par Microsoft, qui vient avec IIS et ASP.NET installé sur Windows Server Core
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie un fichier de l'hôte dans l'image, à un emplacement connu.


