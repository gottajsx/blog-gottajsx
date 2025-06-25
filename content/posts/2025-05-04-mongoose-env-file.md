+++
authors = ["Lone Coder"]
title = "Mongoose Environment File"
date = "2025-05-04"
description = "Mongoose Environment File"
tags = [
    "Atlas", "MongoDB"
]
+++

Pour connecter un backend Express à MongoDB Atlas via Mongoose, tu dois stocker les informations sensibles dans un fichier `.env`. Voici les éléments clés à y placer :

## ✅ Contenu typique du .env :

```bash
MONGODB_URI=mongodb+srv://<USERNAME>:<PASSWORD>@<CLUSTER>.mongodb.net/<DBNAME>?retryWrites=true&w=majority
PORT=3000
```

## 🔐 Détails des variables :

`MONGODB_URI` : L'URL de connexion à MongoDB Atlas.

* Remplace <USERNAME> et <PASSWORD> par ceux de ton utilisateur MongoDB Atlas.

* <CLUSTER> correspond au nom de ton cluster.

* <DBNAME> est le nom de ta base de données.

`PORT` (facultatif) : Le port sur lequel ton serveur Express va écouter.

## 💡 Bonnes pratiques :

Ne jamais commit le `.env` : ajoute-le à `.gitignore`.

Utiliser `dotenv` pour charger les variables dans ton app Express :

```bash
npm install dotenv
```
Dans ton fichier principal (ex. `index.js` ou `app.js`) :

```javascript
require('dotenv').config();
const mongoose = require('mongoose');

mongoose.connect(process.env.MONGODB_URI, {
  useNewUrlParser: true,
  useUnifiedTopology: true
})
.then(() => console.log('Connecté à MongoDB Atlas'))
.catch(err => console.error('Erreur de connexion à MongoDB', err));
```
