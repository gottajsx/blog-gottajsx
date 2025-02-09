+++
authors = ["Lone Coder"]
title = "Differences between JRE and JDK"
date = "2025-01-23"
description = "What are the differences between Java JRE and JDK"
tags = [
    "Java", "JRE", "JDK"
]
+++

## JRE (Java Runtime Environment)

The JRE is a runtime environment used to run Java applications. It includes everything needed to execute Java programs but does not include tools for developing them.

**Components of the JRE**:
* **JVM (Java Virtual Machine)**: The engine that executes Java bytecode.
* **Standard Libraries**: Core Java classes (e.g., `java.lang`, `java.util`, etc.) required to run Java applications.
* **Other Utilities**: Tools like `java` (to launch applications) and `javaw` (for GUI applications).

**When to use the JRE**:
* If you only need to run Java applications (e.g., a `.jar` file).
* If you are not developing or compiling Java code.

## JDK (Java Development Kit)

The JDK is a software development kit used to develop Java applications. It includes everything in the JRE, plus additional tools for compiling, debugging, and developing Java programs.

**Components of the JDK** :
* **JRE**: Everything included in the JRE (JVM, standard libraries, etc.).
* **Java Compiler (̀`javac`)**: Converts Java source code (`.java` files) into bytecode (`.class` files).
* **Development Tools**:
    * `javadoc`: Generates documentation from Java source code comments.
    * `jdb`: A debugger for Java programs.
    * `jar`: Packages Java files into archives (.jar files).
    * `javap`: Disassembles .class files to inspect bytecode.

* **Development Libraries**: Additional APIs for development purposes.

**When to use the JDK**:
* If you are developing Java applications.
* If you need to compile Java code (using `javac`).
* If you need tools for debugging, documentation, or packaging.

