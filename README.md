# Projet403
Binome : 
Kesavan Nanthushan 21109075
Rapin Marine 28600299

Pour ce projet 1 d'OPSCI, on a décider de faire un docker-compose ce qui facilite l'éxecution et la compréhension du projet. Ce projet est composé de deux dossiers principaux, mana et opsci-strapi-frontend

### Prérequis : 

- **Etape 1 : déployer la base de données :** docker run -dit -p 5432:5432 -e POSTGRES_PASSWORD=safepassword -e POSTGRES_USER=strapi --name strapi-pg postgres
  
(Pour déployer la base de données nécessaire à strapi, il faut lancer la commande et configurer son propre mot de passe et username)

- **Etape 2 : créer un projet strapi :** yarn create strapi-app ${project-name}

(il faut suivre les instructions demandés à la suite de cette commande en choissisant le mode avancé puis séléctionné postgresql)

- **Etape 3 : suivre les commande dans le fichier script.sh** 


### mana : 

mana est le dossier qui contient le backend, donc le strapi. Il contient le docker-compose.yml 

### opsci-strapi-frontend : 

opsci-strapi-frontend est le dossier qui contient le frontend.

### INFORMATIONS : 

Pour le frontend :
- **frontend :** opsci-strapi-frontend
- **port du frontend :** 5173
- **adresse IP :** Network : http://192.168.128.2:5173/ et Local : http://localhost:5173/
- **nom du conteneur :** opsci-strapi-frontend-1

Pour le backend : 
- **backend :** mana
- **port du backend :** 1337
- **adresse IP :** http://localhost:1337
- **nom du conteneur :** mana-1

Pour la base de données : 
- **base de données :** PostgreSQL
- **nom du conteneur :** postgres-1


-------------------------------------------

# Projet 2

On souhaite créer un système permettant d’intégrer de grande quantité de données venant de différents flux avec beaucoup de résilience à l’erreur.
Pour ça on utilise un message broker: Kafka. On veut lancer un kafka avec docker

Notre kafka va nécéssiter plusieurs topics :

product : un topic dédié à la création de nouveau produit en masse, venant de différentes sources
event : un topic dédié à la création de nouveau produit en masse, venant de différentes sources
stock : un topic pour enregistrer et appliquer tous les mouvements de stocks de nos produits

Attention tous ces topics devront être précisés dans les configurations des consumers et producers. Si le noms n’est pas le même des deux cotées la communication ne marchera pas.


Listes des conteneurs ajouté : 

- **product-producer**
- **product-consumer**
- **event-producer**
- **event-consumer**
- **stock-producer**
- **stock-consumer**
- **kafka**
- **zookeeper**

Dans ce projet, les producer produisent des élements qu'ils envoient aux consumers via kafka et cela permet de remplir Strapi de ces données. Product rempresente l'ensemble des produits, event represente les evenements et stock permet de gerer le stock.

Les logs de stock-consumer sont dans le fichier logs-stock-consumer.pdf et stock-producer renvoie bien les "messages send succesfully".
