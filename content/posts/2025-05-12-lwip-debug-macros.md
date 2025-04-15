+++
authors = ["Lone Coder"]
title = "LWIP DEBUG Macros"
date = "2025-04-12"
description = "How to Debug using LWIP_DEBUG Macros"
tags = [
    "LWIP", "C"
]
+++

lwIP provides several other debug-related macros besides `LWIP_DEBUGF`. These are useful for logging, tracing, state monitoring, assertions, and customizing how debug info is printed.

Here’s a full breakdown of the most important ones:

## LWIP_DEBUGF(flag, message)

We’ve already talked about this one — it's the main macro for debug printing, conditioned on a specific module's debug flag.

## Debug Flags (used with LWIP_DEBUGF)

These are bit flags used to control what kinds of debug messages get printed:
```C
#define LWIP_DBG_ON             0x80U
#define LWIP_DBG_OFF            0x00U
#define LWIP_DBG_TRACE          0x40U  // Function-level tracing
#define LWIP_DBG_STATE          0x20U  // State changes
#define LWIP_DBG_FRESH          0x10U  // Fresh/unexpected situations
#define LWIP_DBG_HALT           0x08U  // Halt after this debug output
```

You can combine these with OR:
```C
#define MY_DEBUG (LWIP_DBG_ON | LWIP_DBG_TRACE | LWIP_DBG_STATE)
```

Then:
```C
LWIP_DEBUGF(MY_DEBUG, ("Some detailed trace here\n"));
```

## Debug Levels (filtered by LWIP_DBG_MIN_LEVEL)

```C
#define LWIP_DBG_LEVEL_ALL      0x00
#define LWIP_DBG_LEVEL_WARNING  0x01
#define LWIP_DBG_LEVEL_SERIOUS  0x02
#define LWIP_DBG_LEVEL_SEVERE   0x03
```

Set this in `lwipopts.h`:
```C
#define LWIP_DBG_MIN_LEVEL LWIP_DBG_LEVEL_ALL
```

This tells lwIP to ignore debug messages below that level.

## Platform-specific debug/diag macros

These are defined in arch/cc.h, and you can override them for your target (e.g., to print over UART):
```C
#define LWIP_PLATFORM_DIAG(x)      do { printf x; } while(0)
#define LWIP_PLATFORM_ASSERT(x)    do { printf("ASSERT: %s\n", x); abort(); } while(0)
```

You can change these to log somewhere else or halt the system differently.

## Assertions

```C
LWIP_ASSERT("some message", condition);
```

If the condition fails, it calls `LWIP_PLATFORM_ASSERT()` — typically prints a message and halts or breaks.

## Debug Flags Per Module (you enable these in lwipopts.h)

You can turn debug `ON` or `OFF` for specific modules like this:

```C
#define TCP_DEBUG         LWIP_DBG_ON
#define UDP_DEBUG         LWIP_DBG_ON
#define IP_DEBUG          LWIP_DBG_ON
#define ETHARP_DEBUG      LWIP_DBG_ON
#define DHCP_DEBUG        LWIP_DBG_ON
#define DNS_DEBUG         LWIP_DBG_OFF
#define SYS_DEBUG         LWIP_DBG_ON
```

Each module then uses `LWIP_DEBUGF(MODULE_DEBUG, ...)` internally.