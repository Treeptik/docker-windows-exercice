# 

Ex�cutez **docker image build** pour ex�cuter les �tapes dans les Dockerfile :
```
docker image build -t <DockerId>/nerd-dinner-db .
```
```
docker image build -t <DockerId>/nerd-dinner-web .
```

Cr�ez des conteneurs qui utilise les nouvelles images que vous venez de cr�er :

```
docker container run -d -p 1433:1433 --name nerd-dinner-db <DockerId>/nerd-dinner-db
```
```
docker container run -d -p 8081:80 --name nerd-dinner-web <DockerId>/nerd-dinner-web
```
![register-account](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/register-account.PNG)
![sqlconnection](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/sqlconnection.PNG)
![db-NerdDinner](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/db-NerdDinner.PNG)