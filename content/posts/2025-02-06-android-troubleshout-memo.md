+++
authors = ["Lone Coder"]
title = "Android Emulator Troubleshoot Memo"
date = "2025-02-06"
description = ""
tags = [
    "Android"
]
+++

## Restart Adb Server

```bash
adb kill-server
adb start-server
```

## Start Emulator without GPU

```bash
emulator -avd Medium_Phone_API_35 -gpu off
```

## Start Expo

```bash
rm -rf .expo .expo-shared node_modules/.cache
npx expo start
```

As `npx expo start --clear` may lead to error, we first clear the cache, then repeat `npx expo start` with **a** (open Android) and **r** (reload app) 