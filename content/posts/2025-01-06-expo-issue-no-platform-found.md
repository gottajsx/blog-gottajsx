+++
authors = ["Lone Coder"]
title = "Getting Error: 'No platform details found'"
date = "2025-01-04"
description = "Getting Error: 'No platform details found'"
tags = [
    "React-Native", "Tailwindcss", "Nativewind", "Expo"
]
+++

Getting the error `No platform details found

Originates from using `tailwindcss-react-native` in a React Native project. This error indicates that you have not properly configured the `TailwindProvider` component, which is necessary to pass platform information (iOS, Android, or Web) to all parts of the application using `TailwindCSS`.

**Why does this error occur?** 

* Missing `TailwindProvider`:
The `TailwindProvider` component is required by `tailwindcss-react-native` to function. It acts as a context that provides essential platform details, allowing Tailwind to generate the appropriate styles.

* Incorrect configuration of the platform in `TailwindProvider`:
The `TailwindProvider` requires a platform attribute to specify whether the application is running on iOS, Android, or Web.

## Solution 1

Add `TailwindProvider` in your project.

Wrap the main application with the `TailwindProvider` component:

Example : `App.tsx`

```jsx
import { TailwindProvider } from 'tailwindcss-react-native';
import { View, Text } from 'react-native';

export default function App() {
  return (
    <TailwindProvider platform="ios">
      <View className="flex-1 items-center justify-center bg-black">
        <Text className="text-white font-bold text-xl">Hello, Tailwind!</Text>
      </View>
    </TailwindProvider>
  );
}
```

## Solution 2

Configuring dynamically the platform dynamiquement la plateforme.

If we want to automatically detect the platform, use `Platform.OS` from React Native to supply the value to `TailwindProvider`

```jsx
import { TailwindProvider } from 'tailwindcss-react-native';
import { Platform, View, Text } from 'react-native';

export default function App() {
  return (
    <TailwindProvider platform={Platform.OS}>
      <View className="flex-1 items-center justify-center bg-black">
        <Text className="text-white font-bold text-xl">Hello, Tailwind!</Text>
      </View>
    </TailwindProvider>
  );
}
```