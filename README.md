# What is this fork?

It is a renamed fork from a Gradle plugin (which is actually another fork of a deprecated plugin) which now fails to resolve packages from its own expired domain. (**This description is provided for Gradle.org developers who don't really test the derived works and convicts that my plugin fork is meaningless.**)

Packages are renamed as it is being published to (obviously) plugins.gradle.org to avoid name conflicts.

----

# Introduction

This is a gradle plugin which wraps JNAerator for automatically
generating JNA bindings for native libraries.

# Usage:

Gradle 1.x-2.1:

```
buildscript {
    dependencies {
        classpath "org.anarres.gradle:gradle-jnaerator-plugin:1.0.0"
		// https://github.com/etiennestuder/gradle-plugindev-plugin/issues/11
        classpath "com.nativelibs4java:jnaerator:0.11"
    }
}

apply plugin: 'org.anarres.jnaerator'
```

Gradle 2.2+:

```
plugins {
    id 'org.anarres.jnaerator' version '1.0.0'
}
```

Then:

```
jnaerator {
	libraryName 'udev'
	packageName 'org.anarres.jna.udev'
	headerFiles "/usr/include/libudev.h"
	// runtimeMode "JNAerator"
	// define "FOO=bar", "ANSWER=42"
	// extraArgs "-v", "-foo", "-bar"
}
```

# Example:

See https://github.com/shevek/udev4j .

# API Documentation

The [JavaDoc API](http://shevek.github.io/gradle-jnaerator-plugin/docs/javadoc/)
is also available.

