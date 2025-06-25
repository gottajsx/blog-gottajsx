+++
authors = ["Lone Coder"]
title = ""
date = "2025-04-30"
description = "Download Medias from X Using dl-gallery"
tags = [
    "X", "dl-gallery"
]
+++

1. Using gallery-dl (open-source, Python)

* A command-line tool that can download all media from an X account.

* Also supports Instagram, Reddit, and more.

```bash
gallery-dl "https://twitter.com/AccountName"
```
Install it via pip:

```bash
pip install gallery-dl
```
To avoid limitations, you can:

* Log in to X and use your session cookie.

* Add the cookie to gallery-dl config.

## ⚙️ Example: gallery-dl with cookie config

Open X in a browser.

Retrieve your auth_token cookie (via browser dev tools).

Create a file at `~/.config/gallery-dl/config.json`:

```json
{
    "extractor": {
        "twitter": {
            "cookies": {
                "auth_token": "YOUR_COOKIE_HERE"
            }
        }
    }
}
```

Run:
```bash
gallery-dl "https://twitter.com/username"
```