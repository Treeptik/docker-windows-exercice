# Optimiser la taille des images

Exécutez **docker image build** pour exécuter les étapes dans le Dockerfile: 
```
docker image build -t docker image build -t <dockerId>/example-1 .
```
L’image obtenue se compose de trois couches supplémentaires, une pour chaque instruction **RUN**.
```
docker history doc-example-1
IMAGE               CREATED             CREATED BY                                      SIZE                COMMENT
a395ca26777f        15 seconds ago      cmd /S /C powershell.exe -Command Remove-Item   24.56 MB
6c137f466d28        28 seconds ago      cmd /S /C powershell.exe -Command Start-Proce   178.6 MB
957147160e8d        3 minutes ago       cmd /S /C powershell.exe -Command Invoke-WebR   125.7 MB

```
récupérer l'adresse IP du conteneur:
```
$ip = docker container inspect --format '{{ .NetworkSettings.Networks.nat.IPAddress }}' app
```
vous pouvez ouvrir votre navigateur avec l'adresse IP du conteneur et voir le site ASP.NET:

## Poussez vos images sur Docker Hub