+++
authors = ["Lone Coder"]
title = "ES7+ React/Redux/React-Native snippets"
date = "2024-01-02"
description = "ES7+ React/Redux/React-Native snippets"
tags = [
    "React", "React-Native", "Snippets", "Vs Code"
]
+++

[ES7+ React/Redux/React-Native snippets] (https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets&ssr=false#overview) is one of the most used extensions by React and React Native developers. It provides many shorthand prefixes to accelerate development and help developers create code snippets and syntax for React, Redux, GraphQL, and React Native.

## Installation

In VS Code, press **Ctrl+P**, and execute the command `ext install dsznajder.es7-react-js-snippets`.

If not, visit the [VS Code Marketplace] (https://marketplace.visualstudio.com/), search for the **ES7+ React/Redux/React-Native snippets** extension, and install it directly in your local VS Code application.

## Snippets

See [the list of snippets] (https://github.com/r5n-labs/vscode-react-javascript-snippets/blob/HEAD/docs/Snippets.md)

### React Components

#### rfc

```jsx
import React from 'react'

export default function $1() {
  return <div>$0</div>
}
```

#### rfce

```jsx
import React from 'react'

function $1() {
  return <div>$0</div>
}

export default $1
```

### React Native Components

#### rnf

```jsx
import React from 'react'
import { View, Text } from 'react-native'

export default function $1() {
  return (
    <View>
      <Text> $2 </Text>
    </View>
  )
}
````

