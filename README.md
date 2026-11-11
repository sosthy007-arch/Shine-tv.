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
<!doctype html>
<html lang="fr">
<head>
<meta charset="utf-8"><meta name="viewport" content="width=device-width, initial-scale=1">
<meta name="theme-color" content="#080d18"><meta name="description" content="SHINE TV : TV, football, films et séries."><link rel="manifest" href="manifest.webmanifest"><link rel="icon" href="shine-icon.svg" type="image/svg+xml"><meta name="apple-mobile-web-app-capable" content="yes"><meta name="apple-mobile-web-app-status-bar-style" content="black-translucent"><title>Shine TV</title>
<link rel="stylesheet" href="styles.css">
</head>
<body>
<header class="topbar">
  <a class="brand" href="#" aria-label="Shine TV accueil"><span class="brand-mark">✦</span>SHINE<span>TV</span></a>
  <nav id="nav">
    <button class="nav-link active" data-view="home">Accueil</button>
    <button class="nav-link" data-view="tv">TV en direct</button>
    <button class="nav-link" data-view="sports">Football</button>
    <button class="nav-link" data-view="movies">Films & séries</button>
    <button class="nav-link" data-view="favorites">Mes favoris</button>
  </nav>
  <div class="top-actions"><input id="search" type="search" placeholder="Rechercher…" aria-label="Rechercher"><button class="login-trigger" id="loginOpen">Connexion</button><button class="avatar" title="Profil">S</button></div>
</header>
<main>
  <section class="hero" id="hero">
    <div class="hero-content">
      <div class="eyebrow"><span class="live-dot"></span> VOTRE UNIVERS DE DIVERTISSEMENT</div>
      <h1>Tout ce que vous aimez.<br><em>Au même endroit.</em></h1>
      <p>Chaînes en direct, grands matchs, films et séries — découvrez Shine TV.</p>
      <div class="hero-actions"><button class="primary" data-view="tv">Explorer la TV <span>→</span></button><button class="secondary" data-view="movies">Découvrir les films</button></div>
      <small class="note">Aperçu de démonstration · contenus à connecter</small>
    </div>
    <div class="hero-art"><div class="orb orb1"></div><div class="orb orb2"></div><div class="screen"><div class="screen-glow">✦</div><b>SHINE TV</b><small>PLAY YOUR WORLD</small></div></div>
  </section>
  <section class="quick-stats">
    <div><span class="stat-icon">▣</span><span><b>TV en direct</b><small>Vos chaînes préférées</small></span></div>
    <div><span class="stat-icon">⚽</span><span><b>Sports & football</b><small>Les grands rendez-vous</small></span></div>
    <div><span class="stat-icon">▻</span><span><b>Films & séries</b><small>À regarder à votre rythme</small></span></div>
  </section>
  <div id="content"></div>
</main>
<footer><span class="brand small"><span class="brand-mark">✦</span>SHINE<span>TV</span></span><span>Une expérience de streaming, sur vos écrans.</span><span>© 2026 Shine TV · Prototype</span></footer>
<div class="toast" id="toast" role="status"></div>
<div class="modal-backdrop" id="accountModal" aria-hidden="true">
  <section class="account-modal" role="dialog" aria-modal="true" aria-labelledby="accountTitle">
    <button class="modal-close" id="loginClose" aria-label="Fermer">×</button>
    <div class="modal-brand">✦ SHINE<span>TV</span></div>
    <h2 id="accountTitle">Bienvenue sur Shine TV</h2>
    <p class="modal-subtitle">Connectez-vous pour retrouver votre univers.</p>
    <div class="account-tabs"><button class="account-tab active" data-account-tab="login">Connexion</button><button class="account-tab" data-account-tab="register">Créer un compte</button></div>
    <form id="accountForm">
      <label for="accountEmail">Adresse e-mail</label><input id="accountEmail" type="email" placeholder="vous@exemple.com" required>
      <label for="accountPassword">Mot de passe</label><input id="accountPassword" type="password" placeholder="8 caractères minimum" minlength="8" required>
      <button class="primary full" type="submit" id="accountSubmit">Se connecter</button>
    </form>
    <p class="fine-print">Prototype : aucun compte n'est créé et aucune donnée n'est envoyée.</p>
    <div class="plan-mini"><b>Envie de tout regarder ?</b><span>Découvrez nos formules d'abonnement.</span><button id="plansOpen">Voir les abonnements →</button></div>
  </section>
</div>
<div class="modal-backdrop" id="plansModal" aria-hidden="true">
  <section class="plans-modal" role="dialog" aria-modal="true" aria-labelledby="plansTitle">
    <button class="modal-close" id="plansClose" aria-label="Fermer">×</button>
    <div class="modal-brand">✦ SHINE<span>TV</span></div>
    <h2 id="plansTitle">Choisissez votre formule</h2>
    <p class="modal-subtitle">Des offres à définir selon votre catalogue et vos droits de diffusion.</p>
    <div class="plan-grid">
      <article class="plan-card"><span class="plan-name">ESSENTIEL</span><h3>Découverte</h3><p>TV et sélection de contenus</p><ul><li>Accès sur un écran</li><li>Favoris personnels</li></ul><button class="secondary plan-select" data-plan="Découverte">Choisir</button></article>
      <article class="plan-card featured"><span class="plan-name">POPULAIRE</span><h3>Premium</h3><p>Une expérience complète</p><ul><li>TV, sports et catalogue VOD</li><li>Plusieurs profils</li></ul><button class="primary plan-select" data-plan="Premium">Choisir</button></article>
      <article class="plan-card"><span class="plan-name">FAMILLE</span><h3>Famille</h3><p>Pour tous vos écrans</p><ul><li>Profils familiaux</li><li>Contrôle parental prévu</li></ul><button class="secondary plan-select" data-plan="Famille">Choisir</button></article>
    </div>
    <p class="fine-print">Les prix, paiements et activations seront configurés avant le lancement. Aucun paiement réel n'est activé dans cette maquette.</p>
  </section>
</div>
<script src="app.js"></script><script>if ("serviceWorker" in navigator) window.addEventListener("load", () => navigator.serviceWorker.register("./sw.js").catch(console.error));</script>
</body></html>
