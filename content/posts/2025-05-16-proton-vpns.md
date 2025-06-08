+++
authors = ["Lone Coder"]
title = "How to Use ProtonVPN on Linux"
date = "2025-04-16"
description = "How to Use ProtonVPN on Linux"
tags = [
    "VPN"
]
+++

## Step 1: Sign Up for ProtonVPN

Go to the ProtonVPN website:
👉 https://protonvpn.com

Create a free account (or upgrade to a paid one if needed).

## Step 2: Install ProtonVPN Client (Recommended)

ProtonVPN offers an official command-line client for Linux. Let’s set it up:
For Ubuntu/Debian:

**Update your package list**

```bash
sudo apt update && sudo apt upgrade
```

**Install required dependencies**

```bash
sudo apt install -y wget apt-transport-https
```

**Import ProtonVPN’s public key**

```bash
wget -q -O - https://repo.protonvpn.com/debian/public_key.asc | sudo apt-key add -
```

**Add the ProtonVPN repository**

```bash
echo 'deb https://repo.protonvpn.com/debian stable main' | sudo tee /etc/apt/sources.list.d/protonvpn.list
```

**Update package list again**

```bash
sudo apt update
```

**Install the ProtonVPN CLI**

```bash
sudo apt install protonvpn-cli
```

## Step 3: Log In

Open a terminal and log in:

```bash
protonvpn-cli login YOUR_USERNAME
```

Replace `YOUR_USERNAME` with the username you used to sign up.

You’ll be prompted to enter your password.

## Step 4: Connect to the VPN

* To connect quickly (best server):

```bash
protonvpn-cli connect
```
* To connect to a specific country:

```bash
protonvpn-cli connect --cc US
```

(Replace US with your desired country code, like FR for France.)

## Step 5: Disconnect from the VPN

```bash
protonvpn-cli disconnect
```

## Optional Settings

✅ Check VPN status:

```bash
protonvpn-cli status
```
✅ Enable kill switch (to block all traffic if VPN disconnects):

```bash
protonvpn-cli ks --on
```

(Use `--off` to disable it.)

✅ Check help:

```bash
protonvpn-cli --help
```

## Alternative: OpenVPN Manual Setup

ProtonVPN also provides .ovpn files you can download from your account dashboard. You can then use OpenVPN manually:

```bash
sudo openvpn --config path/to/config.ovpn
```

But the CLI client is easier to use and recommended.
