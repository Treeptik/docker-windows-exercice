# exercice-1

Préparez et exécutez une application personnalisée à l'aide de Docker
Jetez un oeil au Dockerfile pour cette application, qui crée un simple site Web ASP.NET en cours d'exécution qui affiche le nom d'hôte du serveur. Il n'y a que deux instructions:
* FROM spécifie l'image à utiliser comme point de départ pour cette image. 
  Microsoft / aspnet est une image détenue par Microsoft, avec IIS et ASP.NET installé sur Windows Server Core
* COPY copie un fichier de l'hôte dans l'image, à un emplacement connu.
* titi