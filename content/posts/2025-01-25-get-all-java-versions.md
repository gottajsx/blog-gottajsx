+++
authors = ["Lone Coder"]
title = "Get all Java Versions on Linux System"
date = "2025-01-25"
description = "How to get all the java version on a Linux system"
tags = [
    "Java", "JRE", "JDK"
]
+++

## Check Available Versions in Official Repositories (Ubuntu/Debian)

On Ubuntu or Debian-based systems, you can list all available Java versions in the official repositories using:

```bash
apt list openjdk-* jdk-*
```

This will show you all OpenJDK and Oracle JDK versions available for installation.

## Install Specific Java Versions

You can install specific versions of Java using the package manager. For example:

* **OpenJDK 8**:

```bash
sudo apt install openjdk-8-jdk
```
* **OpenJDK 11**:

```bash
sudo apt install openjdk-11-jdk
```

* **OpenJDK 17**:

```bash
sudo apt install openjdk-17-jdk
```

## Use a PPA for Additional Versions

If the version you need isn’t in the official repositories, you can add a PPA (Personal Package Archive) to access more versions. For example:

* Add the OpenJDK PPA:

```bash
sudo add-apt-repository ppa:openjdk-r/ppa
sudo apt update
```

* Install the desired version:

```bash
sudo apt install openjdk-19-jdk  # Example for OpenJDK 19
```

## Use SDKMAN! (Cross-Platform)

`SDKMAN!` is a powerful tool to manage multiple versions of Java (and other SDKs) on any platform (Linux, macOS, Windows).

* Install SDKMAN!:

```bash
curl -s "https://get.sdkman.io" | bash
source "$HOME/.sdkman/bin/sdkman-init.sh"
```

* List all available Java versions:

```bash
sdk list java
```

* Install a specific version:

```bash
sdk install java 17.0.5-oracle  # Example for Oracle JDK 17
```

* Switch between installed versions:

```bash
sdk use java 11.0.17-open
```

## Check Installed Versions

To see which Java versions are already installed on your system:

```bash
update-alternatives --list java
```

If nothing shows up, it means no Java versions are managed by `update-alternatives`. You can add them manually using:

```bash
sudo update-alternatives --install /usr/bin/java java /path/to/java/bin/java 1
```