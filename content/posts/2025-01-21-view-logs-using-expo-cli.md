+++
authors = ["Lone Coder"]
title = "View Logs using Expo CLI"
date = "2025-01-21"
description = "Learn how to view logs when using Expo CLI, native logs in Android Studio and Xcode, and system logs"
tags = [
    "Expo", "ReactNative", "Logs"
]
+++

Logging information in a React Native app works similarly to in a web browser. You can use `console.log`, `console.warn` and `console.error`. However, at times, you might want to dive deep to get more useful information about what's happening in your app. For that, you can use native logs and system logs.

## Console logs

When you run `npx expo start` and connect a device, console logs will show up in the terminal process. These logs are sent from the runtime to Expo CLI over web sockets, meaning the results are lower fidelity than connecting dev tools directly to the engine.

You can view high fidelity logs and use advanced logging functions like `console.table` by creating a development build with Hermes, and connecting the inspector.

## Native logs

You can view native runtime logs in Android Studio and Xcode by compiling the native app locally. 

## System logs

While it's usually not necessary, if you want to see logs for everything happening on your device, for example, even the logs from other apps and the OS, you can use the following commands:

```bash
# show system logs for android device
npx react-native log-android

# show system logs for IOS device
npx react-native log-ios
```

## Procedure Reminding

1. Ensure `@react-native-community/cli` is enable on your system, so that `package.json` contains:
```json
  "devDependencies": {
    "@react-native-community/cli": "latest",
```

2. Start ``npx react-native log-android (or `npx react-native log-ios`) in a first terminal

3. Start app in a second terminal using `npx expo start --clear`