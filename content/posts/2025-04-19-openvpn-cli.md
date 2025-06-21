+++
authors = ["Lone Coder"]
title = "OpenVPN Linux CLI"
date = "2025-04-19"
description = "OpenVPN CLI"
tags = [
    "VPN"
]
+++

## OpenVPN CLI

To use OpenVPN CLI, simply type the following command on bash shell

```bash
sudo openvpn --config ~/vpn/votre-config.ovpn
```

## Username and Password Memorization

**Solution: Using an `auth.txt` file**

Create a text file containing your username and password. For example, create a file called `auth.txt` in your VPN folder:

```bash
nano ~/Documents/VPN/auth.txt
```

Add the following two lines:

```bash
your_username
your_password
```

Save and close the file (Ctrl+O, Enter, then Ctrl+X in Nano).

Edit your .ovpn (or .conf) file:

Add (or uncomment) the following line:

```bash
auth-user-pass auth.txt
```

Or adjust the line so that it points to your auth.txt file.

Start OpenVPN with:

```bash
sudo openvpn --config ~/Documents/VPN/your-config.ovpn
```

🔒 Important Security Note

➡️ Your `auth.txt` file contains your password in plain text!
➡️ Make sure it’s only readable by you:

```bash
chmod 600 ~/Documents/VPN/auth.txt
```
