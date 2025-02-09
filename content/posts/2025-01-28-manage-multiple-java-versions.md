+++
authors = ["Lone Coder"]
title = "Manage Multiple Java Versions"
date = "2025-01-28"
description = "How to manage multiple Java versions"
tags = [
    "Java", "JRE", "JDK"
]
+++

## Step 1 — Installing Java

One option for installing Java is to use the version packaged with Ubuntu. By default, Ubuntu 22.04 includes Open JDK 11, which is an open-source variant of the JRE and JDK.

To install the OpenJDK version of Java, first update your `apt` package index:

```bash
sudo apt update
```

Next, check if Java is already installed:
```bash
java -version
```

If Java is not currently installed, execute the following command to install the JRE from OpenJDK 11:
```bash
sudo apt install default-jre
```

The JRE will allow you to run almost all Java software.

Verify the installation with:
```bash
java -version
```

You may need the JDK in addition to the JRE in order to compile and run some specific Java-based software. To install the JDK, execute the following command, which will also install the JRE:
```bash
sudo apt install default-jdk
```

Verify that the JDK is installed by checking the version of javac, the Java compiler:
```bash
javac -version
```

## Step 2 — Managing Java

You can have multiple Java installations on one server. You can configure which version is the default for use on the command line by using the `update-alternatives` command.

```bash
sudo update-alternatives --config java
```

This is what the output would look like if you’ve installed multiple versions of Java:
```bash
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                         Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      auto mode
  1            /usr/lib/jvm/java-11-openjdk-amd64/bin/java   1111      manual mode
* 2            /usr/lib/jvm/java-11-oracle/bin/java          1091      manual mode

Press <enter> to keep the current choice[*], or type selection number:
```

Choose the number associated with the Java version to use it as the default, or press `ENTER` to leave the current settings in place.

You can do this for other Java commands, such as the compiler (`javac`):
```bash
sudo update-alternatives --config javac
```

Other commands for which this command can be run include, but are not limited to: `keytool`, `javadoc`, and `jarsigner`.

## Step 3 — Setting the JAVA_HOME Environment Variable

Many programs written using Java use the `JAVA_HOME` environment variable to determine the Java installation location.

To set this environment variable, first determine where Java is installed. Use the `update-alternatives` command:
```bash
sudo update-alternatives --config java
```

Copy the path from your preferred installation. Then open `/etc/environment` using `nano` or your favorite text editor:
```bash
sudo nano /etc/environment
```

At the end of this file, add the following line, making sure to replace the highlighted path with your own copied path, and to not include the bin/ portion of the path:

```bash
JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
```

Modifying this file will set the `JAVA_HOME` path for all users on your system.

Save the file and exit the editor.

Now reload this file to apply the changes to your current session:
```bash
source /etc/environment
```

Verify that the environment variable is set:
```bash
echo $JAVA_HOME
```