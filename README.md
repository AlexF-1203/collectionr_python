# CollectionR

Application de gestion de collections de cartes Pokémon et autres TCG.

## Prérequis

- Docker
- Docker Compose
- WSL2 (pour Windows)

## Configuration avec Docker

### Variables d'environnement

Créez un fichier `.env` à la racine du projet avec les variables suivantes :

```
POKEMON_TCG_API_KEY=votre_cle_api_pokemon_tcg
DEBUG=1
SECRET_KEY=dev_secret_key_a_changer_en_production
DATABASE_URL=postgres://postgres:postgres@db:5432/collectionr
REDIS_URL=redis://redis:6379/0
ALLOWED_HOSTS=localhost,127.0.0.1
CORS_ALLOWED_ORIGINS=http://localhost:5173,http://127.0.0.1:5173
```

Remplacez `votre_cle_api_pokemon_tcg` par votre clé API Pokemon TCG.

### Démarrage de l'application

1. Construire les images Docker :

```bash
docker-compose build
```

2. Démarrer les services :

```bash
docker-compose up
```

3. Accéder à l'application :
   - Frontend : http://localhost:5173
   - Backend API : http://localhost:8000
   - Admin Django : http://localhost:8000/admin

### Commandes utiles

- Démarrer les services en arrière-plan :

```bash
docker-compose up -d
```

- Arrêter les services :

```bash
docker-compose down
```

- Voir les logs :

```bash
docker-compose logs -f
```

- Exécuter des commandes Django :

```bash
docker-compose exec backend python manage.py <commande>
```

- Créer un superutilisateur Django :

```bash
docker-compose exec backend python manage.py createsuperuser
```

- Exécuter des commandes npm :

```bash
docker-compose exec frontend npm <commande>
```

## Développement

- Le code du backend se trouve dans le dossier `backend/`
- Le code du frontend se trouve dans le dossier `frontend/`

Les modifications apportées au code sont automatiquement prises en compte grâce aux volumes Docker, sans avoir à redémarrer les conteneurs. 