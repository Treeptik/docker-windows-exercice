# exercice-1

Pr�parez et ex�cutez une application personnalis�e � l'aide de Docker
Jetez un oeil au Dockerfile pour cette application, qui cr�e un simple site Web ASP.NET en cours d'ex�cution qui affiche le nom d'h�te du serveur. Il n'y a que deux instructions:
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - sp�cifie l'image � utiliser comme point de d�part pour cette image. 
  Microsoft / aspnet est une image d�tenue par Microsoft, avec IIS et ASP.NET install� sur Windows Server Core
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - copie un fichier de l'h�te dans l'image � un emplacement connu.
