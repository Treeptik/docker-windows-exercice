# Optimiser la taille des images

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t docker image build -t <dockerId>/example-1 .
```
L’image obtenue se compose de trois couches supplémentaires, une pour chaque instruction **RUN**.
```
docker history example-1

IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
a395ca26777f        15 seconds ago      cmd /S /C powershell.exe -Command Remove-Item   24.56 MB
6c137f466d28        28 seconds ago      cmd /S /C powershell.exe -Command Start-Proce   178.6 MB
957147160e8d        3 minutes ago       cmd /S /C powershell.exe -Command Invoke-WebR   125.7 MB

```
Ouvrir votre Dockerfile dans le dossier exercice-0 et remplacer le contenu du fichier par les instructions ci-dessous.
```
# escape=`
FROM windowsservercore

RUN powershell.exe -Command `
  $ErrorActionPreference = 'Stop'; `
  Invoke-WebRequest https://www.python.org/ftp/python/3.5.1/python-3.5.1.exe -OutFile c:\python-3.5.1.exe ; `
  Start-Process c:\python-3.5.1.exe -ArgumentList '/quiet InstallAllUsers=1 PrependPath=1' -Wait ; `
  Remove-Item c:\python-3.5.1.exe -Force
```
Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t docker image build -t <dockerId>/example-2 .
```
L’image obtenue se compose de quatre couches:
```
docker history doc-sample-2

IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
ddf43b1f3751        6 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   127.2 MB
d43abb81204a        7 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   66.46 MB
7a21073861a1        7 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   115.8 MB
6801d964fda5        5 months ago
```
Pourquoi allons-nous préférer cette organisation dans le Dockerfile ?