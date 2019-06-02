---
layout: post
title: Scala setup
---

This post is about setting up [scala](https://www.scala-lang.org/) on a mac machine using scala build tool([sbt](https://www.scala-sbt.org/)) and a standalone system wide installation using [homebrew](https://brew.sh/).

### Java SDK must be installed

Run ```javac -version```, javac version should be greater than 1.8 or higher otherwise download and install the JDK from [here](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

### Install scala and start scala REPL through sbt

```
brew update && brew install sbt@1
```

Now to install scala with specific version run the following commands

```
mkdir foo-build
cd foo-build
touch build.sbt
```

Add ```scalaVersion := "2.12.8"``` in ```build.sbt``` file and run ```sbt console```, this will start the scala REPL, to exit type ```:quit``` or use ```CTRL + D```.

### Install Standalone Scala

```
brew update && brew install scala
```

Now to start scala REPL run ```scala``` and to exit from console type ```:quit``` or use ```CTRL + D```.
