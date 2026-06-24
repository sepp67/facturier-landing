# facturier-landing

Landing page publique du projet **Facturier** — page de présentation statique,
servie par Nginx.

Ce dépôt ne contient aucune logique applicative ni de génération de factures :
il s'agit uniquement de la page d'accueil marketing du projet, qui renvoie
vers l'application de démonstration hébergée séparément (dépôt
[`facturier-app`](https://github.com/sepp67/facturier-app)).
Vous pouvez consulter la landing page sur [`facturier.lavallee.tech`](https://facturier.lavallee.tech).
## Contenu

```
facturier-landing/
├── index.html       # Page unique, HTML/CSS autonome (pas de JS, pas de backend)
├── nginx.conf        # Configuration Nginx du conteneur
└── Dockerfile         # Build de l'image Nginx + contenu statique
```

## Lancer en local

```bash
docker build -t facturier-landing .
docker run --rm -p 8080:80 facturier-landing
```

Accès : [http://localhost:8080](http://localhost:8080)

## Publication de l'image

L'image est publiée automatiquement sur GHCR à chaque push sur `main` ou à
chaque tag `v*`, via `.github/workflows/publish-ghcr.yml`.

**Image publiée :** `ghcr.io/sepp67/facturier-landing:latest`

## Déploiement

Le déploiement en staging et production est géré exclusivement par le dépôt
[devops_staging_prod_infra](https://github.com/sepp67/devops_staging_prod_infra).

Ce dépôt ne contient pas de logique de déploiement, de rôle Ansible, ni de
variables d'environnement.
