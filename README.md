# Coach Renfo

Appli web (PWA) de séances de renforcement avec timers façon Tabata : éditeur de séances et de circuits,
catalogue d'exercices illustrés, exécuteur plein écran avec bips, export d'une séance en `.html` autonome.

Tout est statique : `index.html`, `manifest.json`, `sw.js`, icônes. Les séances sont enregistrées dans le
navigateur de l'appareil (`localStorage`) ; utilise la sauvegarde JSON pour les transférer.

## Tester en local

```bash
python3 -m http.server 8000
```

Puis ouvrir http://localhost:8000.

## Déployer sur GitHub Pages

1. Créer un dépôt GitHub (le nom fait partie de l'URL, par exemple `renfo-x7k2`), puis le relier et pousser :
   ```bash
   git remote add origin git@github.com:<utilisateur>/<depot>.git
   git push -u origin main
   ```
2. Sur GitHub : **Settings → Pages → Build and deployment** : source « Deploy from a branch »,
   branche `main`, dossier `/ (root)`.
3. Après une minute, l'appli est sur `https://<utilisateur>.github.io/<depot>/`.
4. Sur Android (Chrome) : menu ⋮ → **Ajouter à l'écran d'accueil**. L'appli s'ouvre en plein écran et marche hors-ligne.

Le site GitHub Pages est public. Il ne contient aucune donnée personnelle (le code seulement) ;
`noindex` et `robots.txt` évitent l'indexation par les moteurs de recherche. Ne commite jamais de
sauvegarde JSON ni de séance exportée.

## Mettre à jour

Un `git push` sur `main` redéploie. Pour forcer les téléphones à prendre la nouvelle version,
incrémenter `CACHE` dans `sw.js` (`coach-renfo-v1` → `v2`).
