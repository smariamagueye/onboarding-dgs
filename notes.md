# Notes TP Docker et Git — Onboarding DGS Groupe 3

## TP 1 — Lancer mon premier conteneur
J'ai exécuté `docker run hello-world` qui a téléchargé l'image et affiché 
un message de bienvenue. Avec `docker ps -a` j'ai vu que le conteneur 
s'était arrêté automatiquement après son exécution.

## TP 2 — Lancer un serveur web
J'ai lancé un conteneur nginx mappé sur le port 8080. En ouvrant 
http://localhost:8080 j'ai vu la page d'accueil de nginx. J'ai consulté 
les logs avec `docker logs montest` puis arrêté et supprimé le conteneur.

## TP 3 — Entrer dans un conteneur
J'ai utilisé `docker exec -it montest2 sh` pour entrer dans le conteneur. 
J'ai exploré le dossier `/usr/share/nginx/html` et vu les fichiers par défaut 
de nginx. J'ai ensuite nettoyé avec `docker rm -f montest2`.

## TP 4 — Créer ma propre image
J'ai créé un `index.html` et un `Dockerfile` avec `FROM nginx:alpine` et 
`COPY index.html`. Après `docker build` et `docker run`, j'ai vu mon titre 
"Ma premiere image Docker" sur http://localhost:8080.

## TP 5 — Docker Compose
J'ai créé un `docker-compose.yml` avec un service nginx sur le port 8080. 
Après `docker compose up -d` j'ai vu la page nginx sur le navigateur. 
J'ai arrêté avec `docker compose down`.

## Défi — Le disque est plein

**Fichier qui saturait :** `/app/logs/debug_old.log` (200 Mo de données vides)

**Comment j'ai libéré l'espace :**
Je suis entré dans le conteneur avec `docker compose exec app sh`, 
j'ai identifié le fichier lourd avec `du -sh /app/logs/*`, 
puis je l'ai supprimé avec `rm /app/logs/debug_old.log`.

**Résultat :** Le script `sh /app/run.sh` a affiché 
"OK : l'application a pu écrire."
