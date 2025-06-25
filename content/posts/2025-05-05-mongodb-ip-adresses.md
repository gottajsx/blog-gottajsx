+++
authors = ["Lone Coder"]
title = "MongoDB Atlas Authorized IPs"
date = "2025-05-05"
description = "Mongoose Environment File"
tags = [
    "Atlas", "MongoDB"
]
+++

Pour changer les adresses IP autorisées sur MongoDB Atlas, suis ces étapes (via l’interface web) :

## 🌐 Étapes via l’interface MongoDB Atlas

1. Connecte-toi à MongoDB Atlas.

2. Sélectionne ton projet et ton cluster.

3. Va dans l’onglet "Network Access" (ou "Accès réseau") dans le menu de gauche.

4. Tu verras une liste d’adresses IP autorisées.

5. Clique sur "Add IP Address" (ou "Ajouter une adresse IP").

        🔢 Pour autoriser une IP spécifique : entre-la manuellement (ex. 123.45.67.89).

        🌍 Pour autoriser toutes les IPs : entre 0.0.0.0/0 (attention : moins sécurisé).

        🖥 Pour autoriser ton IP actuelle : clique sur "Add Current IP Address".

6. Clique sur "Confirm" ou "Save" pour enregistrer.

## 🛠️ Modifier ou supprimer une IP

Pour modifier : tu dois supprimer l’entrée existante et en ajouter une nouvelle.

Pour supprimer une IP : clique sur l’icône corbeille à droite de l’adresse IP dans la liste.

🕒 Remarque

* Après l’ajout ou le retrait d'une IP, il peut y avoir un court délai de propagation (~1 minute).

* Assure-toi que le pare-feu local ou de ton hébergeur autorise aussi les connexions sortantes vers MongoDB Atlas.
