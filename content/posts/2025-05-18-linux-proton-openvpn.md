+++
authors = ["Lone Coder"]
title = "How to Manually Configure OpenVPN for Proton VPN in Linux"
date = "2025-04-18"
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

1. Go to Settings **Settings → Network → VPN → +**

![ovpn-1](/images/ovpn-linux-nm-1.webp)



2. Select **Import from file…** and use your default file manager to **Open** the OpenVPN configuration file you downloaded earlier. 

![ovpn-2](/images/ovpn-linux-nm-2.webp)


3. Go to **Authentication** and enter your OpenVPN Username and Password into the relevant fields. Click **Add** when you’re done 

![ovpn-3](/images/ovpn-linux-nm-3.webp)

4. Back at **Settings → Network → VPN, toggle** the switch next to the OpenVPN connection you just set up to **on**. You can configure as many connections as you like.

![ovpn-4](/images/ovpn-linux-nm-4.webp)

You’re now connected to Proton VPN. To verify this, visit [the free secure IP scanner](https://protonvpn.com/what-is-my-ip-address). Since this is a manual connection, you should also check DNS leaks.

![geo-locator](/images/ip-geo-lovator.png)