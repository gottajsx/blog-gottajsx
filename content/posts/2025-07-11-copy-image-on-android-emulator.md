+++
authors = ["Lone Coder"]
title = "How to Copy Images on Android Emulator"
date = "2025-07-11"
description = "How to Copy Images on Android Emulator"
tags = [
    "Android", "Emulator"
]
+++

**1. Vérifie que ton émulateur est bien lancé et détecté :**

```bash
adb devices
```

Tu devrais voir une ligne avec `emulator-5554` (ou un autre port).

**2. Copie ton image depuis l’hôte Ubuntu vers l’émulateur avec :**

```bash
adb -s emulator-5554 push /chemin/vers/image.png /sdcard/Download/
```
`/chemin/vers/image.png` = chemin absolu ou relatif de ton fichier sur Ubuntu
`/sdcard/Download/` = dossier dans lequel tu veux la mettre (accessible ensuite depuis l’app "Files" de l’émulateur)

⚠️ adapte `emulator-5554` si ton adb devices te donne un autre ID.


**3. Vérifie que l’image est bien copiée :**

```bash
adb -s emulator-5554 shell ls /sdcard/Download/
```

**👉 Astuce :**

si tu ne veux pas préciser `-s emulator-5554` à chaque fois (parce qu’il n’y a qu’un seul émulateur connecté), tu peux simplement faire :

```bash
adb push /chemin/vers/image.png /sdcard/Download/
```