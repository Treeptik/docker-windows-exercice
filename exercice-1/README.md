# Construire une image de site web simple

Ex�cutez **docker image build** pour ex�cuter les �tapes dans le Dockerfile: 
```
docker image build -t docker image build -t <dockerId>/hostname-app .
```
```
docker container run -d -p 80:80 --name app <dockerId>/hostname-app
```