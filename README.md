# Timeline CSV / ICS

Application autonome (un seul fichier `index.html`, aucune dépendance de build) pour visualiser des événements issus de CSV et/ou d'exports `.ics` sous forme de frise chronologique ou de calendrier.

## Déploiement sur GitHub Pages (plan gratuit)

Aucune compilation, aucun serveur : il suffit d'héberger le fichier statique.

### Étapes

1. **Créer un dépôt GitHub**
   - Sur github.com → **New repository**.
   - Nommez-le comme vous voulez (ex. `mon-planning`).
   - Cochez **Public** (obligatoire pour GitHub Pages sur le plan gratuit — les dépôts privés nécessitent un plan payant pour Pages).

2. **Ajouter les fichiers**
   - Glissez `index.html` et `.nojekyll` dans le dépôt (bouton **Add file → Upload files** sur github.com), puis **Commit**.
   - `.nojekyll` est un fichier vide qui empêche GitHub de traiter le site avec Jekyll (inutile ici, mais évite tout comportement surprenant).

3. **Activer GitHub Pages**
   - Dans le dépôt : **Settings → Pages**.
   - Sous **Build and deployment → Source**, choisissez **Deploy from a branch**.
   - Sous **Branch**, choisissez `main` et le dossier `/ (root)`, puis **Save**.

4. **Patienter ~1 minute**
   - Le site devient accessible à :
     `https://<votre-nom-utilisateur>.github.io/<nom-du-depot>/`
   - L'URL exacte est aussi rappelée en haut de la page Settings → Pages une fois le déploiement terminé.

### Mettre à jour le site plus tard

Remplacez simplement `index.html` par une nouvelle version (upload direct sur github.com, ou `git add`/`commit`/`push` si vous utilisez Git en ligne de commande) — le site se met à jour automatiquement en moins d'une minute, sans configuration supplémentaire.

## Ce qui change (en mieux) par rapport à un usage local (`file://`)

- **Géocodage plus fiable** : les requêtes vers l'API Open-Meteo (dégradé jour/nuit) fonctionnent de façon plus cohérente depuis une vraie origine `https://`, contrairement à l'ouverture locale du fichier où certains navigateurs/réseaux peuvent bloquer les requêtes.
- **Sauvegarde locale (localStorage) plus stable** : elle est liée à l'URL `https://votre-utilisateur.github.io/...`, donc fiable d'une visite à l'autre, y compris depuis un autre appareil ayant visité la même URL (la donnée elle-même reste locale à chaque navigateur, elle n'est pas synchronisée entre appareils).
- **Partage facile** : il suffit d'envoyer le lien — plus besoin de transmettre le fichier HTML lui-même.

## Limites à connaître

- Le stockage (CSV/ICS importés) reste **propre à chaque navigateur** ; il n'y a pas de compte ni de synchronisation multi-appareils.
- GitHub Pages gratuit exige un **dépôt public** : n'importe qui connaissant l'URL peut consulter la page (mais pas vos données importées, qui ne quittent jamais votre navigateur — rien n'est envoyé à un serveur, hormis l'appel de géocodage optionnel vers Open-Meteo).
