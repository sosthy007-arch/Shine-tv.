# SHINE TV — prototype installable (PWA)

Cette version ajoute les bases d'une Progressive Web App (PWA) : icône, manifeste, affichage autonome et cache de base pour ouvrir l'interface hors connexion après un premier chargement.

## Tester sur Android
1. Héberger le contenu du dossier `web` sur un site HTTPS (par exemple GitHub Pages).
2. Ouvrir l'adresse HTTPS dans Google Chrome sur Android.
3. Ouvrir le menu ⋮ puis choisir **Installer l'application** ou **Ajouter à l'écran d'accueil** (le libellé dépend de Chrome).
4. Lancer SHINE TV depuis la nouvelle icône.

## Limites actuelles
C'est une première version installable pour tester l'interface, pas encore une application de streaming complète ni un APK/AAB Android natif. Les comptes, mots de passe, abonnements, paiements, flux TV, matchs, films et séries ne sont pas opérationnels. Le cache hors connexion concerne les fichiers de l'interface, pas des vidéos.

Avant tout lancement, il faudra développer un serveur sécurisé, une vraie authentification, un lecteur vidéo, un catalogue/back-office et intégrer uniquement des chaînes et vidéos dont SHINE TV détient les droits de diffusion. Une version Android native pourra ensuite être générée à partir de cette base et testée avant toute publication Google Play.
