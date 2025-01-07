+++
authors = ["Lone Coder"]
title = "Getting Error: 'Use process(css).then(cb) to work with async plugins'"
date = "2025-01-04"
description = "Getting Error: 'Use process(css).then(cb) to work with async plugins'"
tags = [
    "React-Native", "Tailwindcss", "Nativewind", "Expo"
]
+++

Getting the error `Use process(css).then(cb) to work with async plugins`

Here the code:
```jsx
import { View, Text } from 'react-native'
import React from 'react'

export default function HomeScreen() {
  return (
    <View>
      <Text className="text-red">HomeScreen</Text>
    </View>
  )
}
```

## Solution 1

I solved this error by changing the version to 3.3.2 and using `yarn` instead of `npm`.

Here are the commands I followed:
```bash
yarn add nativewind
yarn add --dev tailwindcss@3.3.2
```

## Solution 2

I have also got the same error when I install the `tailwindcss` with npm.

I have solved this by downgrading the tailwindcss to 3.3.2
```bash
npm install tailwindcss@3.3.2 --save-dev
```
or, as `--dev` is not an option for `NPM`, use 
```bash
npm i -D tailwindcss@3.3.2
```

## Solution n 3

In your `HomeScreen.js` file, wrap the relevant code using the `process(css).then(cb)` pattern mentioned in the error message. Here is an example of how you could modify your code:

```jsx
import { View, Text } from 'react-native';
import React from 'react';
import process from 'tailwindcss/lib';
import styles from './styles.css';

export default function HomeScreen() {
  return (
    <View>
      <Text className="text-red">HomeScreen</Text>
    </View>
  );
}

// Async plugins processing
process(styles)
  .then(() => {
    // Render your components after tailwindcss plugins have been processed
    ReactDOM.render(<HomeScreen />, document.getElementById('root'));
  })
  .catch((error) => {
    console.error(error);
  });
```

## Solutions links

See the following links for reference:

https://stackoverflow.com/questions/76688256/getting-error-use-processcss-thencb-to-work-with-async-plugins

https://www.youtube.com/watch?v=0MLloLPNzy8




