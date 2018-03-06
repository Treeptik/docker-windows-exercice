# Optimiser la vitesse de génération

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t <dockerId>/sample-1 .
```
L’image obtenue se compose de trois couches supplémentaires, une pour chaque instruction **RUN**.
```
docker history <dockerId>/sample-1

IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
a395ca26777f        15 seconds ago      cmd /S /C powershell.exe -Command Remove-Item   24.56 MB
6c137f466d28        28 seconds ago      cmd /S /C powershell.exe -Command Start-Proce   178.6 MB
957147160e8d        3 minutes ago       cmd /S /C powershell.exe -Command Invoke-WebR   125.7 MB

```
Ouvrir votre Dockerfile dans le dossier exercice-0.2 et remplacer le contenu du fichier par les instructions ci-dessous.
```
# escape=`
FROM microsoft/windowsservercore

RUN powershell -Command `
    $ErrorActionPreference = 'Stop'; `
    wget https://www.apachelounge.com/download/VC15/binaries/httpd-2.4.29-Win32-VC15.zip -OutFile c:\apache.zip ; `
    Expand-Archive -Path c:\apache.zip -DestinationPath c:\ ; `
    Remove-Item c:\apache.zip -Force

RUN powershell -Command `
    $ErrorActionPreference = 'Stop'; `
    wget "https://download.microsoft.com/download/1/6/B/16B06F60-3B20-4FF2-B699-5E9B7962F9AE/VSU_4/vcredist_x86.exe" -OutFile c:\vcredist.exe ; `
    start-Process c:\vcredist.exe -ArgumentList '/quiet' -Wait ; `
    Remove-Item c:\vcredist.exe -Force

RUN powershell -Command `
    $ErrorActionPreference = 'Stop'; `
    wget http://windows.php.net/downloads/releases/php-5.6.34-nts-Win32-VC11-x86.zip -OutFile c:\php.zip ; `
    Expand-Archive -Path c:\php.zip -DestinationPath c:\php ; `
    Remove-Item c:\php.zip -Force
```
Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t <dockerId>/sample-2 .
```
L’image obtenue se compose de quatre couches:
```
docker history <dockerId>/doc-sample-2

IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
ddf43b1f3751        6 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   127.2 MB
d43abb81204a        7 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   66.46 MB
7a21073861a1        7 days ago          cmd /S /C powershell -Command  Sleep 2 ;  Inv   115.8 MB
6801d964fda5        5 months ago
```
Pourquoi allons-nous préférer cette organisation dans le Dockerfile ?

Étant donné que chaque instruction ```RUN``` a été exécutée dans sa propre couche, les exécutions suivantes de ce fichier Dockerfile ou d’un ensemble identique d’instructions d’un autre fichier Dockerfile utilisent la couche d’image mise en cache, ce qui réduit le temps de génération.

![alt text](https://github.com/Treeptik/docker-windows-exercice/tree/master/exercice-Dockerfile/opti-vitesse/image/cache-dockerfile.png)
