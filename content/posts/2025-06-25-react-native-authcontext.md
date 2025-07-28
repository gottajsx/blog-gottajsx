+++
authors = ["Lone Coder"]
title = "Utiliser AuthContext Expo"
date = "2025-06-04"
description = "Utiliser AuthContext Expo"
tags = [
    "expo", "react-native", "authcontext"
]
+++

Utiliser `AuthContext` dans un projet **React Native** avec Expo est une façon courante de gérer l’authentification à l’aide du Context API de React. Cela te permet de partager l’état d’authentification (utilisateur connecté, token, etc.) dans toute l’application, sans avoir à passer manuellement les props.

## Etapes Principales

1. Créer un `AuthContext`

2. Créer un `AuthProvider` pour gérer l’état

3. Utiliser le contexte dans tes composants

4. Protéger les routes selon l’état d’authentification

## Arborescence Typique

```bash 
/your-app
│
├── App.js
├── contexts/
│   └── AuthContext.js
├── screens/
│   ├── LoginScreen.js
│   ├── HomeScreen.js
├── navigation/
│   └── AppNavigator.js
```

## Créer le `AuthContext` (`contexts/AuthContext.js`)

```jsx
import React, { createContext, useState, useEffect } from 'react';

export const AuthContext = createContext();

export const AuthProvider = ({ children }) => {
  const [user, setUser] = useState(null); // ou {} si tu préfères
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    // TODO: check local storage / token at launch
    setLoading(false);
  }, []);

  const login = async (username, password) => {
    // Simule un login
    const fakeUser = { id: 1, username };
    setUser(fakeUser);
  };

  const logout = () => {
    setUser(null);
  };

  return (
    <AuthContext.Provider value={{ user, login, logout, loading }}>
      {children}
    </AuthContext.Provider>
  );
};
```

## Utiliser le `AuthProvider` dans `App.js`

```jsx
import React from 'react';
import { AuthProvider } from './contexts/AuthContext';
import AppNavigator from './navigation/AppNavigator';

export default function App() {
  return (
    <AuthProvider>
      <AppNavigator />
    </AuthProvider>
  );
}
```

## Navigation conditionnelle (`AppNavigator.js`)

```jsx
import React, { useContext } from 'react';
import { NavigationContainer } from '@react-navigation/native';
import { createNativeStackNavigator } from '@react-navigation/native-stack';
import { AuthContext } from '../contexts/AuthContext';
import LoginScreen from '../screens/LoginScreen';
import HomeScreen from '../screens/HomeScreen';
import { ActivityIndicator, View } from 'react-native';

const Stack = createNativeStackNavigator();

export default function AppNavigator() {
  const { user, loading } = useContext(AuthContext);

  if (loading) {
    return (
      <View style={{ flex: 1, justifyContent: 'center', alignItems: 'center' }}>
        <ActivityIndicator size="large" />
      </View>
    );
  }

  return (
    <NavigationContainer>
      <Stack.Navigator>
        {user ? (
          <Stack.Screen name="Home" component={HomeScreen} />
        ) : (
          <Stack.Screen name="Login" component={LoginScreen} />
        )}
      </Stack.Navigator>
    </NavigationContainer>
  );
}
```

## Utiliser `login` et `logout` dans les écrans

**LoginScreen.js**

```jsx
import React, { useContext, useState } from 'react';
import { View, TextInput, Button } from 'react-native';
import { AuthContext } from '../contexts/AuthContext';

export default function LoginScreen() {
  const { login } = useContext(AuthContext);
  const [username, setUsername] = useState('');
  const [password, setPassword] = useState('');

  return (
    <View style={{ padding: 20 }}>
      <TextInput placeholder="Username" onChangeText={setUsername} value={username} />
      <TextInput placeholder="Password" secureTextEntry onChangeText={setPassword} value={password} />
      <Button title="Login" onPress={() => login(username, password)} />
    </View>
  );
}
```

**HomeScreen.js**

```jsx
import React, { useContext } from 'react';
import { View, Text, Button } from 'react-native';
import { AuthContext } from '../contexts/AuthContext';

export default function HomeScreen() {
  const { user, logout } = useContext(AuthContext);

  return (
    <View style={{ padding: 20 }}>
      <Text>Bienvenue {user?.username} !</Text>
      <Button title="Logout" onPress={logout} />
    </View>
  );
}
```



