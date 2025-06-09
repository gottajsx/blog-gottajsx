+++
authors = ["Lone Coder"]
title = "How to manually configure OpenVPN for Proton VPN in Linux"
date = "2025-04-16"
description = "Configure OpenVPN for Proton VPN"
tags = [
    "VPN"
]
+++

OpenVPN is a battle-tested, open-source VPN protocol used by our Linux VPN app and Linux CLI. 

## Preparing for OpenVPN

1. An OpenVPN configuration file

Sign in to [account.protonvpn.com}(account.protonvpn.com) go to **Downloads → OpenVPN** configuration files, and download an OpenVPN configuration file for Linux.

2. Your OpenVPN username and password

While still signed in to [account.protonvpn.com}(account.protonvpn.com), go to **Account → OpenVPN / IKEv2 username** to view your OpenVPN username and password. Note that these are not your regular Proton Account username and password.

## How to use OpenVPN with NetworkManager

This is the recommended way to manually configure OpenVPN if your distribution supports NetworkManager(new window).

This guide was created using Ubuntu 22.04, but the instructions are very similar on any system that supports NetworkManager. If your desktop environment uses NetworkManager, there’s a good chance that it already supports OpenVPN. If it doesn’t, you can easily install OpenVPN support in NetworkManager:

On Debian and Ubuntu-based distributions, enter:
```bash
sudo apt-get install network-manager-openvpn-gnome
```
Log out of your Linux session, then log in again for the changes to take effect. 

Once NetworkManager supports OpenVPN, you can configure it. To do this:
![supabase_project_creation](/images/supabase_setup-100225_1.webp)
