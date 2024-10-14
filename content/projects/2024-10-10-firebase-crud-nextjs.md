+++
authors = ["Lone Coder"]
title = "Nextjs CRUD Operations with Firebase"
date = "2024-10-10"
description = "Mastering CRUS Operations in Nextjs using Firestore Database"
tags = [
    "git", "ssh"
]
+++

## Requirements

* Yarn (https://yarnpkg.com)
* Visual Studio Code (https://code.visualstudio.com/download)
* Firebase

## Project Setup

Run the following command in your terminal
```bash
yarn create next-app next-firebase-crud
```

* Would you like to use TypeScript? No
* Would you like to use ESLint? Yes
* Would you like to use Tailwind CSS? Yes
* Would you like to use `src/` directory? Yes
* Would you like to use App Router? (recommended)? No
* Would you like to customize the default import alias (@/*)? Yes

## Dependencies Installation

```bash
cd next-firebase-crud
yard add firebase
```
## Firebase Setup

Go to Console https://console.firebase.google.com/u/0/

Type your project name. 

![crud_1](/images/crud_101024_1.webp)

Disable google analytics, click create project

![crud_2](/images/crud_101024_2.webp)

Click continue

![crud_3](/images/crud_101024_3.webp)

Go to cloud firestore, and create database

![crud_4](/images/crud_101024_4.webp)

![crud_5](/images/crud_101024_5.webp)

![crud_6](/images/crud_101024_6.webp)

Go to project setting, then choose web app.

![crud_7](/images/crud_101024_7.webp)

![crud_8](/images/crud_101024_8.webp)

![crud_9](/images/crud_101024_9.webp)