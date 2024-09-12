+++
authors = ["Lone Coder"]
title = "Create your first Expo app"
date = "2024-09-13"
description = "learn how to create a new Expo project and how to get it running"
tags = [
    "ReactNative", "Expo"
]
+++

Let's learn how to create a new Expo project and how to get it running

## Prerequisites

We'll need the following tools to get started:

* Install [Link Expo Go](https://expo.dev/go) on a physical device.
* [NodeJS LTS](https://nodejs.org/en/)Prepare for development by installing the required tools listed under system requirements.

This tutorial also assumes that you have a basic knowledge of JavaScript and React. 

## Initialize a new Expo app

We will use `create-expo-app` to initialize a new Expo app. It is a command line tool that allows us to create a new React Native project with the `expo` package installed. Run the following command in your terminal:
```bash
npx create-expo-app StickerSmash --template blank
cd StickerSmash
```
This command will create a new directory for the project with the name *StickerSmash*. The `create-expo-app` has a `--template` option, which we can use to create and set up a new project with different pre-installed libraries. In this case, we're using the `blank` which installs the minimum required libraries. 

## Install dependencies
To run the project on the web, we need to install the following dependencies that will help to run the project on the web:
```bash
npx expo install react-dom react-native-web @expo/metro-runtime
```

## Run the app on mobile and web
In the project directory, run the following command to start a development server from the terminal:
```bash
npx expo start
```
Run the app on mobile and web

In the project directory, run the following command to start a development server from the terminal:
npx expo start

Once the development server is running, the easiest way to launch the app is on a physical device with `Expo Go`.

To see the web app in action, press `w` in the terminal. It will open the web app in the default web browser.

