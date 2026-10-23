# Rood Woko – Ma Boutique : projet PWA + APK Android

## Ce que contient le projet
| Fichier | Rôle |
|---|---|
| index.html | L'application complète (ventes, dépenses, commandes clients, fournisseurs, stock, crédits/avances, sauvegarde) |
| manifest.webmanifest | Fiche PWA (nom, couleurs, icônes) |
| sw.js | Service worker : l'application marche sans internet |
| icon-192.png, icon-512.png, icon-maskable-512.png, icon-1024.png | Icônes |
| debug.keystore | Clé de signature fixe : permet de mettre à jour l'APK sans perdre les données |
| .github/workflows/build-apk.yml | Robot GitHub qui fabrique l'APK (copie visible : WORKFLOW-A-COPIER.txt) |

Technologie : application web (HTML/JS) → **PWA** + emballage Android avec **Capacitor 6**, compilé gratuitement par **GitHub Actions**. Aucun ordinateur nécessaire.

## 1. Récupérer les fichiers sur le téléphone
1. Télécharge `rood-woko-projet.zip` depuis la conversation.
2. Ouvre l'application **Fichiers** (ou *Files by Google*) → **Téléchargements**.
3. Appuie sur le zip → **Extraire**. Tu obtiens un dossier `rood-woko`.

## 2. Créer le dépôt GitHub (gratuit)
1. Dans Chrome, va sur github.com et crée un compte (ou connecte-toi).
2. Touche **+** → **New repository**. Nom : `rood-woko`. Choisis **Public**. Touche **Create repository**.
3. Touche **uploading an existing file** (ou *Add file → Upload files*).
4. Touche **choose your files**, ouvre le dossier extrait et sélectionne **tous les fichiers** : index.html, manifest.webmanifest, sw.js, les 4 icônes, debug.keystore, LISEZ-MOI.md. (Ne cherche pas le dossier .github : il est caché, on le crée à l'étape 4.)
5. Touche **Commit changes**.

## 3. Option A : installer comme PWA (le plus rapide)
1. Dans le dépôt : **Settings → Pages**. *Source* : **Deploy from a branch**, branche **main**, dossier **/(root)**, puis **Save**.
2. Attends 1 à 2 minutes. Le lien est : `https://TON-NOM.github.io/rood-woko/`
3. Ouvre ce lien dans **Chrome** → menu **⋮** → **Installer l'application** (ou *Ajouter à l'écran d'accueil*). L'icône verte apparaît sur ton écran.

## 4. Option B : fabriquer l'APK
1. Dans le dépôt : **Add file → Create new file**.
2. Dans le champ du nom, tape exactement : `.github/workflows/build-apk.yml` (les « / » créent les dossiers tout seuls).
3. Ouvre `WORKFLOW-A-COPIER.txt` sur ton téléphone, copie tout le texte et colle-le dans le grand champ de GitHub.
4. Touche **Commit changes**. Le robot démarre tout seul.
5. Va dans l'onglet **Actions** : tu vois « Build APK » en cours (jaune). Attends 5 à 10 minutes jusqu'au **✓ vert**.
6. Retourne sur la page principale du dépôt → **Releases** (colonne de droite, ou en bas sur téléphone) → ouvre la dernière → touche **app-debug.apk** pour le télécharger.
7. Ouvre le fichier téléchargé → autorise **l'installation depuis cette source** si le téléphone le demande → **Installer**.

Si une croix rouge ❌ apparaît dans Actions : ouvre l'exécution, copie le message d'erreur et envoie-le à Claude.

## 5. Mettre à jour plus tard
Remplace `index.html` dans le dépôt (*ouvrir le fichier → crayon ✏ → coller → Commit*). La PWA se met à jour seule. Pour l'APK, relance : **Actions → Build APK → Run workflow**, puis télécharge le nouvel APK et installe-le **par-dessus** l'ancien (grâce à debug.keystore, tes données sont conservées).

## 6. Important : les données
- Les données sont enregistrées **sur le téléphone**, séparément pour la version Claude, la PWA et l'APK.
- La **synchronisation avec le compte Claude** ne marche que dans la version ouverte depuis Claude. Dans la PWA et l'APK, le bouton du haut affiche « Sur cet appareil ».
- Pour transférer tes données de la version Claude vers l'APK/PWA : dans la version Claude, accueil → **Sauvegarder** ; dans la nouvelle application, accueil → **Restaurer** → colle le texte.
- Fais une **sauvegarde régulière** et garde le texte dans une note ou sur WhatsApp.
- L'APK est une version « debug » : parfaite pour ton usage, mais pas pour le Play Store.
