+++
authors = ["Lone Coder"]
title = "Install Aurora Store inside Waydroid"
date = "2025-04-25"
description = "Install Aurora Store inside Waydroid"
tags = [
    "Waydroid"
]
+++

Aurora Store est une alternative libre et open source au Google Play Store, qui te permet de télécharger et installer des applications Android directement depuis les serveurs du Play Store, sans avoir besoin des services Google.


⚠️ Prérequis

* Une distribution Linux (Ubuntu, Arch, Debian, etc.)

* Waydroid installé et fonctionnel

* Connexion Internet active

* Compte Google (optionnel si tu veux utiliser Aurora Store à la place)


## ✅ Étape 1 : Vérifier que Waydroid fonctionne

Ouvre un terminal et tape :

```bash
waydroid session start
```

Puis lance Waydroid :

```bash
waydroid show-full-ui
```

Si l'interface Android se lance correctement, c’est bon.


## ✅ Étape 2 : Installer Aurora Store (alternative au Play Store)

Télécharge Aurora Store APK ici :
    https://auroraoss.com/download/

Transfère l’APK dans Waydroid :
```bash
waydroid app install ~/Téléchargements/aurora-store.apk
```

Lance Aurora Store via l’interface Android de Waydroid. Ainsi, Une fois l'interface Android affichée :

* Glisse vers le haut ou appuie sur le bouton en bas (comme dans Android standard) pour ouvrir le tiroir d'applications.

* Cherche "Aurora Store" dans la liste.

* Appuie dessus pour le lancer.

Lors du premier lancement, tu auras deux options :

* Connexion anonyme (recommandé pour plus de confidentialité)

* Connexion avec compte Google (nécessite un compte secondaire pour limiter les risques)

Connecte-toi anonymement ou avec ton compte Google.
