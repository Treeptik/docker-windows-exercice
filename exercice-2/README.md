# Cr�ez et ex�cutez une image de site Web plus complexe

Pour l'exemple suivant, le Dockerfile est une meilleure repr�sentation d'un script du monde r�el. 

Ce sont les principales caract�ristiques:
	
* [FROM](https://docs.docker.com/engine/reference/builder/#from) - Sp�cifie l'image � utiliser comme point de d�part pour cette image. 
Microsoft / aspnet est une image d�tenue par Microsoft, qui vient avec IIS et ASP.NET install� sur Windows Server Core
* [COPY](https://docs.docker.com/engine/reference/builder/#copy) - Copie un fichier de l'h�te dans l'image, � un emplacement connu.


