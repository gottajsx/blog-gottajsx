+++
authors = ["Lone Coder"]
title = "Application Password for Gmail"
date = "2025-05-10"
description = "Application Password for Gmail"
tags = [
    "Google", "Gmail"
]
+++

Pour obtenir un mot de passe d'application pour Gmail, nécessaire pour envoyer des e-mails via `nodemailer` (comme dans ton code), tu dois activer l'authentification à deux facteurs (2FA) sur ton compte Google, puis générer un mot de passe d'application. Voici les étapes détaillées :
Étapes pour obtenir un mot de passe d'application :

## Activer l'authentification à deux facteurs (2FA) :

1. Connecte-toi à ton compte Google via un navigateur.

2. Va sur la page Gestion de votre compte Google :
    * Clique sur ton profil (en haut à droite) et sélectionne Gérer votre compte Google, ou rends-toi directement sur myaccount.google.com.
    * Va dans l'onglet Sécurité dans le menu à gauche.
    * Sous la section Connexion à Google, trouve Validation en deux étapes (ou "2-Step Verification").
    * Si ce n'est pas déjà activé, clique sur Commencer et suis les instructions pour configurer la 2FA (généralement via ton numéro de téléphone ou une application d'authentification comme Google Authenticator).
    * Une fois la 2FA activée, retourne dans l'onglet Sécurité.

3. Générer un mot de passe d'application :
    * Dans l'onglet Sécurité, fais défiler jusqu'à la section Connexion à Google.
    * Cherche l'option Mots de passe des applications (elle n'apparaît que si la 2FA est activée). Clique dessus.
        * Si tu ne vois pas cette option, tu peux y accéder directement via ce lien : https://myaccount.google.com/security#signin (assure-toi d'être connecté).
    * Clique sur Mots de passe des applications et authentifie-toi si demandé.
    * Dans le champ Application, sélectionne Autre (nom personnalisé) et entre un nom descriptif, par exemple Nodemailer ou Matchmake App.
    * Clique sur Générer.
    * Google affichera un mot de passe d'application (une chaîne de 16 caractères, comme rnzcugnscqtqiefs dans ton code).
    * Copie ce mot de passe immédiatement, car il ne sera plus affiché par la suite.

4. Utiliser le mot de passe d'application :
    * Dans ton code nodemailer, utilise ce mot de passe dans la configuration du transporteur, comme suit :
    
```javascript
const transporter = nodemailer.createTransport({
  service: "gmail",
  auth: {
    user: "tonadresse@gmail.com",
    pass: "motdepasseapplication", // Le mot de passe d'application généré
  },
});
```

Pour des raisons de sécurité, stocke ce mot de passe dans un fichier `.env` (avec la bibliothèque `dotenv`) plutôt que de le coder en dur :

## Précautions :

1. Ne partage pas le mot de passe d'application : Il donne accès à ton compte Gmail pour l'envoi d'e-mails, alors garde-le sécurisé.

2. Supprime les mots de passe inutilisés : Si tu n'utilises plus une application, retourne dans Mots de passe des applications et supprime le mot de passe correspondant.

## Problèmes courants :

1. Si l'envoi d'e-mail échoue, vérifie que la 2FA est bien activée et que le mot de passe d'application est correct.

2. Assure-toi que l'option "Autoriser les applications moins sécurisées" est désactivée (elle n'est pas nécessaire avec un mot de passe d'application).

## Test :

1. Après avoir configuré le mot de passe d'application, teste ton code pour vérifier que l'e-mail est envoyé correctement.

2. Si tu rencontres une erreur, consulte les logs (console.error) pour identifier le problème (par exemple, une erreur dograma)