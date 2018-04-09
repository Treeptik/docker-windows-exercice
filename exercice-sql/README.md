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
Acc�dez au conteneur Web. 
Vous pouvez cliquer sur le bouton Register et enregistrer un compte:
![register-account](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/register-account.PNG)

Sqlectron est un bon client SQL l�ger que vous pouvez utiliser pour vous connecter au conteneur:
![sqlconnection](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/sqlconnection.PNG)

Ensuite, vous pouvez vous connecter � la base de donn�es � l'aide d'un client SQL et interroger la table UserProfile. Vous verrez le nouvel utilisateur:
![db-NerdDinner](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/db-NerdDinner.PNG)