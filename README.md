# Laravel Web Project - Docker Setup

Ce projet utilise Docker pour simplifier l'installation de l'environnement Laravel.

## 🚀 Installation rapide

1. **Cloner le projet**
   ```bash
   git clone <votre-url-du-depot>
   cd web_project
   ```

2. **Préparer les fichiers d'environnement**
   À la racine du projet :
   ```bash
   cp .env.example .env
   ```
   Dans le dossier `web_project/` :
   ```bash
   cp web_project/.env.example web_project/.env
   ```
   *(Pensez à éditer ces fichiers si vous souhaitez changer les mots de passe de la base de données).*

3. **Lancer les conteneurs Docker**
   Assurez-vous que Docker Desktop (ou le moteur Docker) est lancé sur votre machine.
   ```bash
   docker-compose up -d --build
   ```

4. **Installer les dépendances PHP (Composer)**
   ```bash
   docker exec laravel-app-12-apache-php composer install
   ```

5. **Générer la clé d'application Laravel**
   ```bash
   docker exec laravel-app-12-apache-php php artisan key:generate
   ```

6. **Lancer les migrations de la base de données**
   ```bash
   docker exec laravel-app-12-apache-php php artisan migrate
   ```

7. **Installer les dépendances JS et compiler les assets**
   ```bash
   docker exec laravel-app-12-apache-php npm install
   docker exec laravel-app-12-apache-php npm run build
   ```

## 🌐 Accès à l'application

- **Serveur Web (Laravel) :** [http://localhost](http://localhost)
- **Adminer (Base de données) :** [http://localhost:8082](http://localhost:8082)
- **phpMyAdmin :** [http://localhost:8081](http://localhost:8081)

## 🐳 Commandes utiles

- **Arrêter le projet :** `docker-compose down`
- **Lancer le projet :** `docker-compose up -d`
- **Voir les logs :** `docker-compose logs -f`
- **Exécuter une commande artisan :** `docker exec laravel-app-12-apache-php php artisan <commande>`
