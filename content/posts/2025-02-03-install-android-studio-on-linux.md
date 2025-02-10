+++
authors = ["Lone Coder"]
title = "Start Android Emulator from Command Line"
date = "2025-02-05"
description = "How to start Android emulator from command line"
tags = [
    "Android"
]
+++

The Android SDK includes an Android device emulator—a virtual device that runs on your computer. The Android Emulator lets you develop and test Android apps without using a physical device.

## Start the emulator

Use the `emulator` command to start the emulator, as an alternative to running your project or starting it through the AVD Manager.

Here's the basic command-line syntax for starting a virtual device from a terminal prompt:

```bash
emulator -avd avd_name [ {-option [value]} … ]
```

Or
```bash
emulator @avd_name [ {-option [value]} … ]
```

For example, if you launch the emulator from within Android Studio running on a Mac, the default command line will be similar to the following:

```bash
/Users/janedoe/Library/Android/sdk/emulator/emulator -avd Pixel8_API_34 -netdelay none -netspeed full -qt-hide-window -grpc-use-token -idle-grpc-timeout
```

Please note that the arguments `-qt-hide-window` `-grpc-use-token` `-idle-grpc-timeout` are only used to run the emulator window within Android Studio. If you want to run the emulator on its own window, you should not use those extra parameters.

You can specify startup options when you start the emulator, but not after it has started.

For a list of AVD names, enter the following command:
```bash
emulator -list-avds
```

Use this option to display a list of AVD names from your Android home directory. You can override the default home directory by setting the `ANDROID_SDK_HOME` environment variable that specifies the root of the user-specific directory where all configuration and AVD content is stored.

You can set the environment variable in the terminal window before launching a virtual device or through your user settings in the operating system. For example, in your .bashrc file on Linux.

To stop the Android Emulator, close the emulator window.




## Reference Links:

https://developer.android.com/studio/run/emulator-commandline