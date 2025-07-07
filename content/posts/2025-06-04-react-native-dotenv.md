+++
authors = ["Lone Coder"]
title = "React Native Dotenv"
date = "2025-06-04"
description = "React Native Dotenv"
tags = [
    "Dotenv"
]
+++

Mettre l’URL de ton API dans un fichier .env est une bonne pratique pour éviter de hardcoder les valeurs sensibles ou susceptibles de changer (comme l’URL d’un serveur).

Voici comment procéder avec React Native Expo et Axios :

## ✅ 1. Installer react-native-dotenv

Expo (en mode bare workflow ou managed) peut utiliser les variables d’environnement avec Babel.

Installe le package :
```bash
npm install react-native-dotenv
```
ou
```bash
yarn add react-native-dotenv
```


## ✅ 2. Configurer Babel

Dans ton fichier `babel.config.js`, ajoute ceci :

```javascript
module.exports = function(api) {
  api.cache(true);
  return {
    presets: ['babel-preset-expo'],
    plugins: [
      ['module:react-native-dotenv', {
        moduleName: '@env',
        path: '.env',
      }]
    ]
  };
};
```

## ✅ 3. Créer un fichier .env

À la racine de ton projet, crée un fichier .env et ajoute :

```bash
API_URL=http://10.0.2.2:3000
```

## ✅ 4. Utiliser la variable dans ton code

Dans ton fichier JS/TS :

```javascript
import { API_URL } from '@env';
import axios from 'axios';

const response = await axios.get(`${API_URL}/messages`);
```

## ⚠️ Attention

Ne pas mettre d'espaces autour du `=` dans `.env`.

Redémarre Metro bundler si tu changes .env.

Assure-toi que `.env` est bien dans `.gitignore`.

Tu peux aussi créer plusieurs fichiers `.env` comme `.env.development`, `.env.production` si besoin (mais ça demande plus de config).

