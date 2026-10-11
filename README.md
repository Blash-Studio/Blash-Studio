# Blash Studio

Plateforme de jeux vidéo pour découvrir, télécharger et installer des jeux sur ordinateur.
Site statique (HTML, CSS, JavaScript) sans dépendance ni étape de compilation.

## Fonctionnalités

- Thème sombre, responsive (ordinateur, tablette, téléphone)
- Bannière des jeux populaires, sections Populaires, Nouveautés, Gratuits et Recommandés
- Recherche et filtres par genre
- Une page par jeu : description, genre, configuration minimale, taille, version, favoris
- Bouton « Télécharger et installer » : lien vers la page officielle du jeu, ou téléchargement direct avec barre de progression si un fichier autorisé est hébergé
- Comptes (inscription, connexion) et favoris, enregistrés dans le navigateur

## Structure

```
.
├── index.html
├── css/style.css
├── js/app.js          # catalogue (tableau GAMES) et logique du site
├── .github/workflows/pages.yml
├── .nojekyll
├── LICENSE
└── README.md
```

## Lancer en local

Ouvrez `index.html` dans un navigateur, ou lancez un petit serveur :

```bash
python3 -m http.server 8000
```

Puis rendez-vous sur http://localhost:8000.

## Publier sur GitHub Pages

1. Créez un dépôt sur GitHub, puis envoyez-y ce dossier :
   ```bash
   git init
   git add .
   git commit -m "Blash Studio : première version"
   git branch -M main
   git remote add origin https://github.com/VOTRE-COMPTE/blash-studio.git
   git push -u origin main
   ```
2. Dans le dépôt : **Settings > Pages > Source : GitHub Actions**.
3. Chaque `push` sur `main` redéploie le site automatiquement.

## Ajouter un jeu

Ajoutez un objet dans le tableau `GAMES` de `js/app.js` (nom, genres, description, configuration, taille, version, liens). Règles à respecter :

- Ne proposer que des jeux dont la distribution est autorisée (gratuits, open source ou accord de l'éditeur).
- `download` doit pointer vers la page de téléchargement officielle.
- Le champ `file` (URL d'un fichier hébergé avec autorisation, avec CORS activé) active le téléchargement direct et la barre de progression. Sans lui, le bouton ouvre la page officielle.
- Aucun jeu piraté ou fichier sans autorisation.

## Limites actuelles

- Les comptes et favoris sont stockés dans `localStorage` : ils restent sur l'appareil. Des comptes en ligne demandent un back-end (Supabase, Firebase, etc.).
- Tailles, versions et configurations sont indicatives : vérifiez-les sur les sites officiels.
- Les images des jeux sont des illustrations générées, pas les captures officielles.

## Licence

Le code du site est sous licence MIT. Chaque jeu présenté reste soumis à sa propre licence et appartient à ses auteurs.
