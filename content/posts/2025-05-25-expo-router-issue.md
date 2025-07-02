+++
authors = ["Lone Coder"]
title = "expo-router v5.1.0 throws Warning: Invalid prop style supplied to React.Fragment — no Fragment used"
date = "2025-05-25"
description = "expo-router v5.1.0 throws Warning: Invalid prop style supplied to React.Fragment — no Fragment used"
tags = [
    "expo-router", "expo"
]
+++

It must be `expo-router` issue. This happens only on Android for me.

I have edited `node_modules/expo-router/build/views/Navigator.js#152`

```javascript
function DefaultNavigator() {
    // iOS needs flex: 1 style for proper layout
    const isIOS = process.env.EXPO_OS === 'ios';
    
    return (
        <SlotNavigatorWrapper {...(isIOS ? { style: { flex: 1 } } : {})}>
            <SlotNavigator />
        </SlotNavigatorWrapper>
    );
}
```

See https://github.com/expo/expo/issues/37383