# Crazymo
Il s'agit d'un jeu web inspiré par *Tusmo*, lui-même basé sur le jeu *Motus*. Le principe est simple : le joueur doit deviner un mot chargé aléatoirement en un nombre d'essais limité.
Pour chaque essai, il doit saisir un mot existant et les lettres de celui-ci seront colorisées en fonction de leur correspondance avec le mot à trouver.
Dans *Crazymo*, les lettres correspondant exactement avec celles du mot à trouver sont colorées en vert, et celles existant dans le mot mais pas au même emplacement sont colorées en orange.


## Équipe du projet
BORDES Lomé\
SAUVAGET Eliott\
TAIL Rayan\
TRICOT Baptiste\
Groupe **RA1**


## Technologies
<img src="https://user-images.githubusercontent.com/25181517/117207242-07d5a700-adf4-11eb-975e-be04e62b984b.png" alt="Maven" title="Maven" width="30"/> **Maven** / **Java** pour le backend,

<img src="https://user-images.githubusercontent.com/25181517/117448124-a2da9800-af3e-11eb-85d2-bd1b69b65603.png" alt="Vue.js" title="Vue.js" width="30"/> **Vue.js** avec **TypeScript** pour le frontend,

<img src="https://user-images.githubusercontent.com/25181517/117207330-263ba280-adf4-11eb-9b97-0ac5b40bc3be.png" alt="Docker" title="Docker" width="30"/> **Docker** pour conteneuriser le tout,

<img src="https://user-images.githubusercontent.com/25181517/184146221-671413cb-b1ae-47db-a232-b37c99281516.png" alt="SonarQube" title="SonarQube" width="30"/> **SonarQube** pour assurer la qualité de l'application.


## Installation et utilisation
Cloner le projet avec les 2 sous-modules initialisés (backend et frontend) :
```
git clone --recurse-submodules <url-du-repo>
```
Ou bien après un `git clone` classique :
```
git submodule update --init --recursive 
```

Mettre à jour les 2 sous-modules :
```
git submodule update --remote
```

### Backend
Créer un réseau pour utiliser un conteneur :
```
docker network create crazynetwork
```

Construire l'image de la base de données (MariaDB) :
```
docker build -t mariadb-dictionnaire .
```

Démarrer le conteneur MariaDB :
```
docker run --name mariadb-crazymo --network crazynetwork -d -p 3312:3312 mariadb-dictionnaire
```

Lancer le projet sans conteneur :
```
mvn spring-boot:run
```

Lancer le projet avec un conteneur :
```
docker build -t crazymo-back -f dockerfile.back .
docker run --name crazymo-backend --network crazynetwork -d -p 8080:8080 crazymo-back
```

### Frontend
Initialiser Vue.js (après avoir cloné le projet) :
```
cd frontend
npm install
```

Lancer le projet :
```
npm run dev
```

Lancer le conteneur du projet :
```
docker build -t crazymo-front .
docker run --name crazymo-frontend --network crazynetwork -d -p 5173:80 crazymo-front
```


## Retour d'expérience
La réalisation de ce projet a permis de renforcer notre maîtrise de Docker et des systèmes de conteneurisation, en plus de nous avoir appris l'utilisation de SonarQube pour assurer la qualité du code de l'application. Nous avons aussi dû faire preuve d'une certaine rigueur pour appliquer toutes les bonnes pratiques de qualité de développement et pour mettre en place les tests unitaires.