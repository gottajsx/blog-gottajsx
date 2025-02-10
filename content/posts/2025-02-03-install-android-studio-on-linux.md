+++
authors = ["Lone Coder"]
title = "Install Android Studio on a Linux Machine"
date = "2025-01-28"
description = "How to install Android Studio on a Linux machine"
tags = [
    "Android"
]
+++

See pre-requisites on https://developer.android.com/studio/install

Set up Android Studio in just a few clicks. First, check the system requirements. Then download the [latest version of Android Studio](https://developer.android.com/studio).

## Steps to Follow

To install Android Studio on Linux, follow these steps:

* Unpack the `.tar.gz` file you downloaded to an appropriate location for your applications, such as within `/usr/local/` for your user profile or `/opt/` for shared users.

For a 64-bit version of Linux, first install the required libraries for 64-bit machines.

* To launch Android Studio, open a terminal, navigate to the `android-studio/bin/` directory, and execute `studio.sh`.

* Select whether you want to import previous Android Studio settings, then click OK.

* Complete the Android Studio **Setup Wizard**, which includes downloading the Android SDK components that are required for development.

### Required libraries for 64-bit machines 

If you are running a 64-bit version of Ubuntu, you need to install some 32-bit libraries with the following command:

```bash
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1 libbz2-1.0:i386
```

## Environment Variables

You can configure the behavior of Android Studio and the command-line tools by setting environment variables. One of the most useful environment variables to set is `ANDROID_HOME`, which many tools read to determine the Android SDK installation directory. 

To run tools from the command line without including the full path to the executable, set your command search path environment variable to include `ANDROID_HOME/tools`, `ANDROID_HOME/tools/bin`, and `ANDROID_HOME/platform-tools`.

The location of the shell initialization script depends on the shell being used. For Gnu Bash, the location can be `~/.bash_profile` or `~/.bashrc`. For Zsh, the location can be `~/.zprofile`. For TCSH, the location can be `~/.cshrc`.

You can also update the `PATH` environment variable to include the tool locations. So, for Gnu Bash or Zsh:

```bash
export ANDROID_HOME=~/Library/Android/sdk
export PATH=$PATH:$ANDROID_HOME/tools:$ANDROID_HOME/tools/bin:$ANDROID_HOME/platform-tools
```
or

```bash
export ANDROID_HOME=$HOME/Android/Sdk
export PATH=$PATH:$ANDROID_HOME/emulator
export PATH=$PATH:$ANDROID_HOME/tools
export PATH=$PATH:$ANDROID_HOME/tools/bin
export PATH=$PATH:$ANDROID_HOME/platform-tools
```

To verify that all pathes are correctly configure, you can try:
```bash
adb --version
emulator -version
sdkmanager --version
```

## Emulator Environment Variables

By default, the emulator stores configuration files under `$HOME/.android/` and AVD data under `$HOME/.android/avd/`. You can override the defaults by setting the following environment variables. The `emulator -avd <avd_name>` command searches the **avd** directory in the order of the values in `$ANDROID_AVD_HOME`, `$ANDROID_USER_HOME/avd/`, and `$HOME/.android/avd/`.

## Reference Links:

https://developer.android.com/tools/variables