+++
authors = ["Lone Coder"]
title = "No Facing Dating MVP"
date = "2025-07-15"
description = "No Facing Dating"
tags = [
    "Dating"
]
+++

Voici un **planning réaliste et structuré pour créer le MVP** de **No Face Dating** sur **12 semaines (3 mois)**, de l’idéation au lancement bêta. Ce planning est basé sur une petite équipe lean : 
* 1 PM/fondateur, 
* 1 dev mobile, 
* 1 designer, 
* et éventuellement 1 freelance backend ou modération.

## 🛠️ Objectif MVP

L’app doit permettre de :
1. Créer un profil (sans visage)
2. Swiper des profils anonymes
3. Discuter après match
4. Débloquer (optionnellement) le visage après 5 messages

## 🗓️ PLANNING – 12 SEMAINES DE MVP

### Phase 1 – Préparation & Spec (Semaine 1–2)

#### 📌 Semaine 1 – Définition produit

* Définir les features essentielles du MVP (prioriser avec une roadmap simple)
* Écrire les user stories clés : création de profil, upload photo sans visage, swipe, chat, reveal
* Choisir la stack : React Native / Flutter + Firebase pour aller vite
* Identifier outils d’auto-modération (ex : Microsoft Face API, AWS Rekognition, PixLab)

#### 📌 Semaine 2 – UX/UI Design

* Créer les wireframes + flow utilisateurs (Figma)
* Maquettage UI : minimaliste, stylisé, mobile-first
* Prototypage rapide pour tests internes
* Prototypage rapide pour tests internes

#### Livrables :
* Flow utilisateurs clairs
* Prototype Figma cliquable
* Cahier des charges tech light

### Phase 2 – Développement core (Semaines 3–8)

#### 📌 Semaine 3–4 – Auth, profil, upload photo

* Auth via email ou numéro
* Création de profil (nom, âge, style, texte court)
* Upload de 3 à 6 photos (interdiction visage)
* Intégration du filtrage automatique de visage
    * Rejet automatique ou floutage forcé si détection faciale

#### 📌 Semaine 5 – Swiping / matching

* Affichage de profils anonymes (style galerie)
* Swipe right/left
*  Match si les deux ont swipé
* Logging des matchs

#### 📌 Semaine 6–7 – Chat & Reveal

* Système de messagerie simple (type Firebase Chat)
* Blocage auto des images et liens
* Déverrouillage visage après 5 messages échangés mutuellement
    * Animation “défloutage” (optionnelle mais sympa)
    * Permission explicite des deux utilisateurs

#### 📌 Semaine 8 – Backend / sécurisation

* Sécurisation des données utilisateur (Firebase Auth + Firestore rules)
* Dashboard admin simple : modération, signalement, stats
* Analytics de base : taux d’upload valide, matchs, reveal

### Phase 3 – Test, debug, amélioration (Semaines 9–10)

#### 📌 Semaine 9 – Alpha test privé

* 50 à 100 utilisateurs réels (étudiants, Discord, amis)
* Observation des bugs UX / bugs tech
*  Recueillir feedback ciblé : frustration, moments cool, fonctionnalités manquantes

#### 📌 Semaine 10 – Itérations

* Correction bugs critiques
* Simplification des flows trop complexes
* Intégration micro-animations (swipe, match, reveal) si temps

### Phase 4 – Pré-lancement bêta (Semaines 11–12)

#### 📌 Semaine 11 – Préparation lancement

* Créer landing page simple + formulaire d’accès bêta
* Créer visuels TikTok, campagne mail, groupe Discord
* Setup Firebase App Distribution / TestFlight

##### 📌 Semaine 12 – Lancement bêta publique (1000 personnes)

* Campagne TikTok + liste d’attente → distribution accès en vague
* Support utilisateurs, recueil de bugs
* Activation de métriques : taux de match, taux de reveal, temps de conversation
