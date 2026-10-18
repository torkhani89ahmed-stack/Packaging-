# AMANA PACKAGING – APK Android

Application de gestion de stock, ventes et factures, empaquetée en APK avec Capacitor.
GitHub compile l'APK automatiquement : aucun logiciel à installer sur votre ordinateur.

## Créer l'APK (une seule fois)

1. Sur github.com, créez un dépôt **privé** (bouton « New »), par exemple `amana-packaging`.
2. Envoyez-y **tout le contenu de ce dossier**, y compris les dossiers `.github`, `keystore`, `resources` et `www`.
   - Depuis le site : « Add file » > « Upload files », puis glissez les dossiers.
   - Ou avec Git :
     ```
     git init
     git add .
     git commit -m "AMANA PACKAGING"
     git branch -M main
     git remote add origin https://github.com/VOTRE-COMPTE/amana-packaging.git
     git push -u origin main
     ```
3. Ouvrez l'onglet **Actions**. La compilation démarre toute seule (environ 6 à 10 minutes).
   Sinon : Actions > « Build APK » > « Run workflow ».
4. Quand la pastille est verte, ouvrez l'exécution, descendez à **Artifacts** et téléchargez `AMANA-PACKAGING-apk`.
   Décompressez le fichier : vous obtenez `AMANA-PACKAGING.apk`.

Astuce : pour avoir un lien de téléchargement direct, créez un tag, par exemple `v1.0` (Releases > « Create a new release »).
L'APK sera alors joint à la release.

## Installer sur le téléphone

1. Copiez `AMANA-PACKAGING.apk` sur le téléphone (WhatsApp, e-mail, câble ou Drive).
2. Ouvrez le fichier et autorisez « Installer des applications inconnues » si Android le demande.
3. Ouvrez l'application > **Paramètres > Alertes** > activez « Notification sur cet appareil » > **Autoriser**.
4. Touchez **Tester la notification** : elle doit apparaître en haut de l'écran.

Si vous avez refusé l'autorisation par erreur : Réglages Android > Applications > AMANA PACKAGING > Notifications.

## Comment fonctionnent les notifications

- Une notification part tout de suite quand un article passe en rupture ou sous son seuil (par exemple après une vente).
- Tant qu'un article reste en alerte, un rappel est envoyé chaque jour à 8 h, même si l'application est fermée.
  Il s'arrête dès que le stock est réapprovisionné.
- Sur certains téléphones (Xiaomi, Huawei, Oppo, Samsung), il faut aussi désactiver l'économie de batterie pour l'application :
  Réglages > Applications > AMANA PACKAGING > Batterie > « Sans restriction ».

## Mettre à jour l'application

Remplacez `www/index.html` dans le dépôt : GitHub recompile l'APK. Installez le nouvel APK par-dessus l'ancien.
La signature est identique d'une version à l'autre, donc **vos données sont conservées**.

## Vos données

Elles sont enregistrées sur le téléphone uniquement. Faites régulièrement
**Paramètres > Sauvegarde > Exporter** et gardez le fichier hors du téléphone.
Si vous désinstallez l'application, les données sont perdues : exportez d'abord.

## Contenu du dépôt

| Fichier | Rôle |
|---|---|
| `www/index.html` | L'application |
| `capacitor.config.json` | Nom et identifiant de l'application, icône de notification |
| `package.json` | Plugins : notifications, partage, fichiers, bouton Retour |
| `.github/workflows/build-apk.yml` | Compilation automatique de l'APK |
| `resources/` | Icônes de l'application et des notifications |
| `keystore/amana.keystore` | Clé de signature (garder le dépôt privé) |
