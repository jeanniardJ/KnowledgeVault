# Docker

> Category: DevOps
> Scope: Commands and workflows
> Difficulty: Beginner to Intermediate
> Status: Draft

## Purpose

Référence rapide des commandes Docker les plus courantes pour créer, exécuter, inspecter et gérer des conteneurs et des images.

## Installation and version

### Display Docker version

Afficher la version de Docker installée :

```console
docker --version
```

### Display Docker detailed information

Afficher l'aide général de Docker :

```console
docker info
```

### Display command help

```console
docker help
```

Afficher l'aide d'une commande spécifique :

```console
docker run --help
```

## Images

### List local images

Lister les images disponibles localement :

```console
docker image ls
```

### Pull an image

Télécharger une image depuis un registre :

```console
docker pull nginx:latest
```

### Build an image

Construire une image à partir d'un `Dockerfile` :

```console
docker build -t my-app:1.0 .
```

### Tag an image

Ajouter un nouveau tag à une image :

```console
docker tag my-app:1.0 username/my-app:1.0
```

### Remove an image

Supprimer une image locale :

```console
docker image rm my-app:1.0
```

### Inspect an image

Afficher les informations détaillées d'une image :

```console
docker image inspect nginx:latest
```

### Prune unsused images

Supprimer les images inutilisées :

```console
docker image prune
```

> Attention : cette commande peut supprimer des images nécessaires à d'anciens conteneurs.

## Containers

### Run a container

Créer et démarrer un conteneur :

```console
docker run nginx:latest
```

### Run a container in detached mode

Démarrer un conteneur en arrière-plan :

```console
docker run -d --name web-server nginx:latest
```

### Publish a port

Associer un port local au port du conteneur :

```console
docker run -d --name web-server -p 8080:80 nginx:lastest
```

L'application sera accessible sur :

```console
https://localhost:8080
```

### Run an interactive container

Démarrer un conteneur avec un terminal interactif :

```console
docker run -it ubuntu:latest bash
```

### List running containers

Lister les conteneurs en cours d'exécution :

```console
docker container ls
```

### List all containers

Lister tous les conteneurs, y compris ceux qui sont arrêtés :

```console
docker container ls -a
```

### Display container logs

Afficher les journaux d'un conteneur :

```console
docker logs web-server
```

Suivre les journaux en temps réel :

```console
docker logs -f web-server
```

### Display container processes

Afficher les processus exécutés dans conteneur :

```console
docker top web-server
```

### Inspect a container

Afficher les informations détaillées d'un conteneur :

```console
docker inspect web-server
```

### Execute a command

Exécuter une commande dans un conteneur actif :

```console
docker exec web-server nginx -t
```

Ouvrir un terminal dans un conteneur :

```console
docker exec -it web-server sh
```

### Stop container

Arrêter un conteneur :

```console
docker stop web-server
```

### Start a stopped container

Redémarrer un conteneur arrêté :

```console
docker start web-server
```

### Restart a container

```console
docker restart web-server
```

### Remove a container

Supprimer un conteneur arrêté :

```console
docker rm web-server
```

Forcer la suppression d'un conteneur actif :

```console
docker rm -f web-server
```

### Rename a container

```console
docker rename old-name new-name
```

### Copy files

Copier un fichier du système hôte vers un conteneur :

```console
docker cp ./config.json web-server:/app/config.json
```

Copier un fichier du conteneur vers le système hôte :

```console
docker cp web-server:/var/log/app.log ./app.log
```

## Volumes

### List volumes

Lister les volumes Docker :

```console
docker volume ls
```

### Create a volume

Créer un volume nommé :

```console
docker volume create app-data
```

### Mount a volume

Monter un volume dans un conteneur :

```console
docker run -d --name database -v app-data:/var/lib/data \ my-database:1.0
```

### Inspect a volume

Afficher les informations d'un volume :

```console
docker volume inspect app-data
```

### Remove a volume

Supprimer un volume :

```console
docker volume rm app-data
```

> Attention : la suppression d'un volume peut entraîner une perte définitive des données qu'il contient.

## Bind mounts

### Mount a local directory

Monter un dossier local dans un conteneur :

```console
docker run -it -v "$(pwd)":/app node:latest bash
```

Sur Windows PowerShell :

```console
docker run -it -v "$(PWD):/app" node:latest bash
```

Les bind mounts sont utiles pour partager le code source entre la machine locale et le conteneur pendant le développement.

## Networks

### List networks

Lister les réseaux Docker :

```console
docker network ls
```

### Create a network

Créer un réseau :

```console
docker network create app-network
```

### Connect a container to a network

Connecter un conteneur à un réseau :

```console
docker network connect app-network web-server
```

### Run a container on a network

Démarrer un conteneur sur un réseau donné :

```console
docker run -d --name web-server --network app-network nginx:latest
```

### Inspect a network

Afficher les informations d'un réseau :

```console
docker network inspect app-network
```

### Remove a network

Supprimer un réseau :

```console
docker network rm app-network
```

## Docker Compose

### Start services

Démarrer les services définis dans `compose.yaml` :

```console
docker compose up
```

### Build and start services

Reconstruire les images et démarrer les services :

```console
docker composer up  --build
```

### Stop services

Arrêter les services :

```console
docker compose stop
```

### Stop and remove services

Arrêter et supprimer les conteneurs et réseaux du projet :

```console
docker compose down
```

Supprimer également les volumes associés :

```console
docker compose down -v
```

### List Compose services :

Afficher l'état des services :

```console
docker compose ps
```

### Display Compose logs

Afficher les journaux :

```console
docker compose logs
```

Suivre les journaux d'un service :

```console
docker compose logs -f web
```

### Execute a command in a service

Exécuter une commande dans un service actif :

```console
docker compose exec web sh
```

### Validate the compose file

Vérifier la configuration Compose :

```console
docker compose config
```

## Dockerfile

Exemple minimal de `Dockerfile` :

```console
FROM node:22-alpine

WORKDIR /app

COPY package*.json ./

RUN npm ci

COPY . .

CMD ["npm","start"]
```

### Common Dockerfile instructions

| Instruction | Description |
|---|---|
| `FROM` | Définit l’image de base |
| `WORKDIR` | Définit le répertoire de travail |
| `COPY` | Copie des fichiers dans l’image |
| `RUN` | Exécute une commande pendant le build |
| `ENV` | Définit une variable d’environnement |
| `EXPOSE` | Documente le port utilisé par l’application |
| `CMD` | Définit la commande par défaut |
| `ENTRYPOINT` | Définit le processus principal |

## Common workflow

Construire et exécuter une application :

```console
docker build -t my-app:1.0 .
docker run -d --name my-app-container -p 3000:3000 my-app:1.0
docker ps
docker logs -f my-app-container
```

Arrêter et supprimer le conteneur :

```console
docker stop my-app-container
docker rm my-app-container
```

## Cleanup

### Remove stopped containers

Supprimer les conteneurs arrêtés :

```console
docker container prune
```

### Remove unused networks

Supprimer les réseaux inutilisés :

```console
docker network prune
```

### Remove unused volumes

Supprimer les volumes inutilisés :

```console
docker volume prune
```

### Remove unused resources

Supprimer les ressources DOcker inutilisées :

```console
docker system prune
```

Supprimer également les volumes inutilisés :

```console
docker system prune --volumes
```

> Attention : les commandes `prune` peuvent supprimer des ressources encore utiles. Vérifier les ressources ciblées avant de confirmer.

## Security notes

- Utiliser des images officielles ou provenant de sources fiables.
- Éviter d’exécuter les conteneurs avec `--privileged` sans nécessité.
- Ne jamais intégrer de mots de passe ou de tokens dans un `Dockerfile`.
- Utiliser des secrets ou des variables d’environnement adaptées.
- Ajouter un fichier `.dockerignore`.
- Utiliser des images minimales comme les variantes `alpine`
  lorsque cela est compatible avec l’application.
- Scanner les images avant leur déploiement.
- Ne pas exposer inutilement les ports sur toutes les interfaces réseau.

Exemple de `.dockerignore` :

```text
.git
.gitignore
node_modules
.env
*.log
dist
coverage
```

## Troubleshooting

### Display resource usage

Afficher la consommation des conteneurs :

```bash
docker stats
```

### Check port mappings

Vérifier les ports associés à un conteneur :

```bash
docker port web-server
```

### Check disk usage

Afficher l’espace utilisé par Docker :

```bash
docker system df
```

### Check container status

```bash
docker inspect --format="{{.State.Status}}" web-server
```

## Related topics

- Containers
- Images
- Dockerfile
- Docker Compose
- Volumes
- Networks
- Container security
- CI/CD

## Sources

- [Docker Documentation](https://docs.docker.com/)
- [Docker CLI Reference](https://docs.docker.com/reference/cli/docker/)
- [Docker Compose Documentation](https://docs.docker.com/compose/)