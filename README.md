# LomeBordes

C'est un tusmo, un jeu dans lequel on doit deviner un mot un caché en proposant des mots qui se rapprochent le plus du mot secret en termes de lettres correctes et de leur position.


## Cloner le projet avec les 2 sous-modules ( projet backend et frontend ) initialiser 
```
git clone --recurse-submodules <url-du-repo>
```
Ou apres un **git clone**  classique :
```
git submodule update --init --recursive 
```

## Prendre la derniere version des 2 sous-modules
```
git submodule update --remote
```

## Lancer le projet
Demarrer les conteneurs du projet
```
docker compose up -d
```

Apres, lancer le projet via le lien 