+++
authors = ["Lone Coder"]
title = "LWIP_DEBUGF Macro"
date = "2025-04-10"
description = "How to Debug using LWIP_DEBUGF Macro"
tags = [
    "LWIP", "C"
]
+++

## How LWIP_DEBUGF Works in lwIP

The `LWIP_DEBUGF` macro is used in **lwIP (Lightweight IP stack)** to conditionally print debug messages, depending on which debug modules and levels are enabled.

## Basic Syntax

```C
LWIP_DEBUGF(debug_flags, ("format string", args));
```

**Parameters:**

- `debug_flags`: A flag indicating whether this debug message should be printed. These are usually defined in your lwipopts.h file.
-  `("format string", args)`: Like `printf`, this is the message format and any arguments.

## Simple Example

```C
LWIP_DEBUGF(TCP_DEBUG, ("TCP packet received: %d bytes\n", len));
```
This will print the message only if `TCP_DEBUG` is enabled and allowed by the global debug configuration (`LWIP_DBG_MIN_LEVEL`, etc.).

## How to Enable It (in lwipopts.h)

To make `LWIP_DEBUGF` actually do something, you need to:

1. **Enable debugging globally:**

```C
#define LWIP_DEBUG 1
```

2. **Enable specific module debug flags:**

```C
#define TCP_DEBUG      LWIP_DBG_ON
#define IP_DEBUG       LWIP_DBG_OFF
```

3. **Optionally, set the minimum debug level:**

```C
#define LWIP_DBG_MIN_LEVEL  LWIP_DBG_LEVEL_WARNING
```

Also make sure these are set correctly:
* `LWIP_DBG_ON` to enable
* `LWIP_DBG_OFF` to disable
* And levels like `LWIP_DBG_LEVEL_ALL`, `LWIP_DBG_LEVEL_WARNING`, etc.