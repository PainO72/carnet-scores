# 🎲 Carnet de Scores

PWA (Progressive Web App) pour compter les points lors de vos soirées jeux de société.
Installable sur l'écran d'accueil, fonctionne **100% hors-ligne**, sauvegarde locale + sync cloud optionnelle.

Design assorti à l'app Fléchettes : sombre, accents or `#f0c93a`, typo DM Mono / DM Sans.

## ✨ Fonctionnalités

- ➕ Configuration rapide en pills (2 à 8 joueurs, condition de victoire, limite de points)
- 🎯 Score simple, validation manche par manche, annulation
- ⭐ Le leader actuel mis en avant à chaque manche
- 🏁 Limite de points avec barre de progression et alerte rouge au-delà
- 🏆 **Écran de victoire avec confettis** et classement complet
- 📜 **Historique** des parties avec détail manche par manche
- ▶ Reprise automatique si vous quittez en cours de partie
- 💡 **Autocomplete** des noms de jeux et de joueurs
- ☀️🌙 Mode clair / sombre togglable
- 🔗 **Synchronisation cloud** entre appareils (optionnelle, via Firebase)
- 📱 **Installable** sur écran d'accueil (PWA)
- 🌐 Fonctionne **hors connexion**

---

## 🚀 1. Déploiement sur GitHub Pages

1. Créez un nouveau dépôt **public** sur GitHub (par exemple `carnet-scores`).
2. Téléversez **tous les fichiers** de ce dossier à la racine du dépôt.
3. **Settings → Pages** → Source : branche `main`, dossier `/ (root)` → **Save**.
4. Après quelques secondes, ouvrez `https://<votre-pseudo>.github.io/<nom-du-depot>/`.

### Installation sur téléphone

- **iPhone (Safari)** : ouvrez l'URL → bouton **Partager** ↑ → **Sur l'écran d'accueil**.
- **Android (Chrome)** : ouvrez l'URL → menu ⋮ → **Installer l'application**.

---

## 🔗 2. Activer la synchronisation entre appareils (optionnel)

Permet de partager vos parties et noms enregistrés entre votre téléphone, tablette, etc. Tout est gratuit.

### Créer un projet Firebase

1. Allez sur https://console.firebase.google.com
2. **Créer un projet** → nommez-le `carnet-scores` → Continuer
3. Désactivez Google Analytics → **Créer le projet**

### Obtenir la config Firebase

1. Dans le projet : icône ⚙️ → **Paramètres du projet**
2. Section **Vos applications** → cliquez `</>` (Web)
3. Nommez l'app → **Enregistrer**
4. Copiez le bloc `firebaseConfig` affiché à l'écran

### Configurer Firestore

1. Menu gauche : **Firestore Database**
2. **Créer une base de données** → **Démarrer en mode test** → Suivant → **Activer**

### Modifier index.html

Trouvez ce bloc au début du `<script>` (cherchez `FIREBASE_CFG`) :

```javascript
const FIREBASE_CFG = {
  apiKey: "AIzaSyDemo-RemplacezParVotreCle",
  authDomain: "scores-demo.firebaseapp.com",
  projectId: "scores-demo"
};
```

Remplacez par les valeurs de **votre** projet, puis repoussez sur GitHub.

### Utiliser la synchronisation

1. Ouvrez l'app sur vos deux appareils
2. Appuyez sur **« Non synchronisé »** en haut de l'écran
3. Entrez le **même code** (n'importe lequel : `1234`, `42`, etc.) sur les deux appareils
4. Le badge devient vert **« Session 1234 »** → vos parties sont partagées

**Note** : sans configurer Firebase, l'app fonctionne parfaitement en local uniquement.

---

## 📁 Structure

```
.
├── index.html              # Tout en un : structure + styles + logique
├── manifest.json           # Métadonnées PWA
├── sw.js                   # Service Worker (mode hors-ligne)
├── icon-192.png
├── icon-512.png
└── icon-maskable-512.png
```

## 🔧 Tester en local

```bash
python3 -m http.server 8000
# ou : npx serve
```

Puis `http://localhost:8000`.

## 💡 Notes

- Sans sync activée, les données restent dans `localStorage` du navigateur (non partagées entre appareils).
- Avec la sync, les parties et noms sont fusionnés automatiquement à chaque connexion.
- La fusion se base sur l'`id` unique de chaque partie, donc pas de doublons.
- Pour tout effacer : paramètres du navigateur → effacer les données du site.

Bon jeu ! 🎲
