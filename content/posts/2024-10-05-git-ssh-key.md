+++
authors = ["Lone Coder"]
title = "Github New SSH Key Generation"
date = "2024-10-05"
description = "Generation a New SSH Key and Adding it to the ssh-agent"
tags = [
    "git", "ssh"
]
+++

A new SSH key can be generated on a ocal machine. After the key is generated, the public key can be added to an account on `GitHub.com` to enable authentication for Git operations over SSH.

1. Open TerminalTerminalGit Bash.

2. Paste the text below, replacing the email used in the example with a GitHub email address.
```
ssh-keygen -t ed25519 -C "your_email@example.com"
```

3. Start the `ssh-agent` in the background.
```
eval "$(ssh-agent -s)"
```

4. Add the SSH private key to the `ssh-agent`.
```
ssh-add ~/.ssh/id_ed25519
```

For more informations, follow the [officials docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)