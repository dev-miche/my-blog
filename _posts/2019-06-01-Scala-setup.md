---
layout: post
title: Scala setup
---

This post is about setting up [scala](https://www.scala-lang.org/) on a mac machine using scala build tool([sbt](https://www.scala-sbt.org/)) and a standalone system wide installation using [homebrew](https://brew.sh/).

### Java SDK must be installed

Run ```javac -version```, javac version should be greater than 1.8 or higher otherwise download and install the JDK from [here](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).

### Install sbt

```
brew update && brew install sbt@1
```

Run following commands to verify <span style="color:red">sbt</span> installation

```
mkdir foo-build
cd foo-build
touch build.sbt
sbt
```

after running the last ```sbt``` command you will enter into the sbt shell, to leave sbt shell type ```exit``` or use ```CTRL + D```.

### Install Standalone Scala

```
brew update && brew install scala
```

now to open scala REPL console run ```scala``` and to exit from console type ```:quit``` or use ```CTRL + D```.
