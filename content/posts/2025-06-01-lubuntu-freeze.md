+++
authors = ["Lone Coder"]
title = "Enhance Swap Size to Prevent Lubuntu Freezes"
date = "2025-06-21"
description = ""Enhance Swap Size to Prevent Lubuntu Freezes
tags = [
    "Ubuntu", "Swap"
]
+++

Si tu as peu de RAM (< 8 Go), ajouter du swap aide à éviter les freezes.

## Créer un fichier swap (ex. 4 Go) :

```bash
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

## Rendre le swap permanent

Ajoute cette ligne à la fin du fichier `/etc/fstab`

```bash
/swapfile none swap sw 0 0
```

## Verifie si le swap est actif

```bash
swapon --show
```
Si tu vois une ligne comme:
```bash
/swapfile file 4G  1G  -2
```

Alors le swap est déjà actif,et tu ne peux pas modifier ce fichier tant qu'il est utilisé

## Désactiver temporairement le swap

Si tu veux remplacer ou redimensionner le swap, fais d'abord :

```bash
sudo swapoff /swapfile
```

Tu pourras ensuite le recréer

```bash
sudo rm /swapfile
sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
```

## Vérification finale

```bash
swapon --show
free -h
```
Tu devrais maintenant voir 4G de swap disponible.