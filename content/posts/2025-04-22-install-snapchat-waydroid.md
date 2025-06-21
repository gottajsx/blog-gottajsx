+++
authors = ["Lone Coder"]
title = "Install Snapchat with Waydroid [Not for X11]"
date = "2025-04-22"
description = "Install Snapchat With Waydroid"
tags = [
    "Waydroid"
]
+++

## Étape 1 : Installer Waydroid
 
1. Active les modules nécessaires

```bash
sudo apt update
sudo apt install curl ca-certificates -y
curl https://repo.waydro.id | sudo bash
sudo apt install waydroid
```

2. Initialiser Waydroid

```bash
sudo waydroid init
```

✅ Cela télécharge l’image système Android.

3. Démarrer Waydroid

```bash
sudo waydroid container start
waydroid session start
```

📱 L'interface Android va apparaître dans une fenêtre. C’est Android 10 ou 11 tournant nativement sur ton système.

## Étape 2 : Activer le Play Store (facultatif mais recommandé)

Par défaut, Waydroid n'a pas Google Play, donc tu dois :

* Télécharger un script d'activation de microG + Play Store.

* Ou installer l’APK de Snapchat manuellement.

### Option A – Installer Play Store via script (le plus pratique)

```bash
wget https://raw.githubusercontent.com/axel358/waydroid_playstore/main/install-playstore.sh
chmod +x install-playstore.sh
./install-playstore.sh
```

🟢 Une fois terminé, redémarre Waydroid, connecte-toi avec ton compte Google.

## Étape 3 : Installer Snapchat

###  A – Depuis le Play Store (si installé)

* Ouvre Play Store.

* Recherche Snapchat.

* Installe-le comme une app Android classique.

### Option B – Installer l’APK manuellement

* Télécharge l'APK officiel :

        https://www.apkmirror.com/apk/snap-inc/snapchat/ (choisis une version récente)

* Installe adb :

```bash
sudo apt install adb
```

* Connecte Waydroid à ADB :

```bash
adb connect localhost:5555
```

* Installe l’APK :

```bash
adb install snapchat.apk
```

## Étape 4 : Lancer Snapchat

```bash
waydroid app launch org.snapchat.android
```

💡 Ou clique simplement sur l’icône dans le menu de Waydroid.