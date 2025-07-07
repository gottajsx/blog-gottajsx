+++
authors = ["Lone Coder"]
title = "React Native Axios Backend"
date = "2025-06-02"
description = "React Native Axios Backend"
tags = [
    "Axios"
]
+++

En phase de test pour une app React Native, les adresses à utiliser pour communiquer avec ton backend dépendent de l’environnement dans lequel tournent ton backend et ton app mobile. Voici un résumé clair selon les cas :

## 1. Simulateur Android (via Android Studio)

### Backend sur la même machine (localhost) :
➤ Utilise http://10.0.2.2:PORT/
(par exemple : http://10.0.2.2:3000/api)

10.0.2.2 est un alias spécial vers 127.0.0.1 depuis l’émulateur Android.

## 2. Simulateur iOS (via Xcode)

Utilise directement http://localhost:PORT/ ou http://127.0.0.1:PORT/
(exemple : http://localhost:3000/api)

iOS Simulateur partage le réseau de ta machine.

## 3. Appareil physique (connecté au même Wi-Fi)

Récupère l’adresse IP locale de ton ordinateur (où tourne le backend) :
ipconfig (Windows) ou ifconfig (Mac/Linux)

Exemple : 192.168.1.42

Dans ton app React Native :

```javascript
axios.get('http://192.168.1.42:3000/api')
```

## ⚠️ Assure-toi que :

Le pare-feu ne bloque pas la connexion.

Ton backend écoute sur 0.0.0.0 (pas juste localhost) pour être accessible depuis un autre appareil :

```bash
node server.js --host 0.0.0.0
```