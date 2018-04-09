# 

Exécutez **docker image build** pour exécuter les étapes dans les Dockerfile :
```
docker image build -t <DockerId>/nerd-dinner-db .
```
```
docker image build -t <DockerId>/nerd-dinner-web .
```

Créez des conteneurs qui utilise les nouvelles images que vous venez de créer :

```
docker container run -d -p 1433:1433 --name nerd-dinner-db <DockerId>/nerd-dinner-db
```
```
docker container run -d -p 8081:80 --name nerd-dinner-web <DockerId>/nerd-dinner-web
```
Accédez au conteneur Web. 
Vous pouvez cliquer sur le bouton Register et enregistrer un compte:
![register-account](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/register-account.PNG)

Sqlectron est un bon client SQL léger que vous pouvez utiliser pour vous connecter au conteneur:
![sqlconnection](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/sqlconnection.PNG)

Ensuite, vous pouvez vous connecter à la base de données à l'aide d'un client SQL et interroger la table UserProfile. Vous verrez le nouvel utilisateur:
![db-NerdDinner](https://raw.githubusercontent.com/Treeptik/docker-windows-exercice/master/exercice-sql/image/db-NerdDinner.PNG)