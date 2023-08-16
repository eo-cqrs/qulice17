<img alt="logo" src="http://img.qulice.com/logo.svg" width="200px" height="55px"/>

[![EO principles respected here](https://www.elegantobjects.org/badge.svg)](https://www.elegantobjects.org)
[![DevOps By Rultor.com](http://www.rultor.com/b/eo-cqrs/qulice17)](http://www.rultor.com/p/eo-cqrs/qulice17)
[![We recommend IntelliJ IDEA](https://www.elegantobjects.org/intellij-idea.svg)](https://www.jetbrains.com/idea/)

[![mvn](https://github.com/yegor256/qulice/actions/workflows/mvn.yml/badge.svg?branch=master)](https://github.com/yegor256/qulice/actions/workflows/mvn.yml)
[![PDD status](http://www.0pdd.com/svg?name=yegor256/qulice)](http://www.0pdd.com/p?name=yegor256/qulice)
[![Maven Central](https://maven-badges.herokuapp.com/maven-central/com.qulice/qulice/badge.svg)](https://maven-badges.herokuapp.com/maven-central/com.qulice/qulice)
[![codecov](https://codecov.io/gh/yegor256/qulice/branch/master/graph/badge.svg)](https://codecov.io/gh/yegor256/qulice)
![Lines of code](https://img.shields.io/tokei/lines/github/yegor256/qulice)
[![Hits-of-Code](https://hitsofcode.com/github/yegor256/qulice)](https://hitsofcode.com/view/github/yegor256/qulice)
[![License](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/yegor256/qulice/blob/master/LICENSE.txt)

Integrated with JDK17+ by [@EO-CQRS](https://github.com/eo-cqrs)

Qulice is a static analysis quality control instrument for Java
projects. It combines all the best static analysis instruments
and pre-configures them, including
[Checkstyle](https://checkstyle.sourceforge.io/) and
[PMD](https://pmd.github.io/).
You don't need to use and configure them individually anymore.

Read more at [www.qulice.com](https://www.qulice.com).

Also, read this blog post first:
[_Strict Control of Java Code Quality_](https://www.yegor256.com/2014/08/13/strict-code-quality-control.html).

Just add this plugin to your `pom.xml`:

```xml
<build>
  <plugins>
    <plugin>
      <groupId>com.qulice</groupId>
      <artifactId>qulice-maven-plugin</artifactId>
      <configuration>
        <license>file:${basedir}/LICENSE.txt</license>
      </configuration>
      <executions>
        <execution>
          <goals>
            <goal>check</goal>
          </goals>
        </execution>
      </executions>
    </plugin>
  </plugins>
</build>
```

Then, make sure you have the JDK binaries (including the Java compiler `javac`)
accessible from your `PATH` environment variable (e.g. if you have JDK 1.8.0
installed in Windows your PATH should contain something like `C:\Program
Files\Java\jdk1.8.0\bin`).

Also remember that we support Maven version >= 3.1.0.

The path to license has to be declared in the following format:
`file:${basedir}/LICENSE.txt`, it's the default value, one can use any full path
instead of `${basedir}`.

Read this short summary of [typical mistakes](https://github.com/yegor256/qulice/wiki/mistakes)
you may encounter in your project.

In order to download schemas required for XML validation, you might need proxy
setup. Maven proxy is not supported, but standard 
[JVM proxy](https://docs.oracle.com/javase/8/docs/technotes/guides/net/proxies.html)
works fine. To use it just add `-Dhttp.proxyHost=HOST -Dhttp.proxyPort=PORT`
to your `MAVEN_OPTS` environment variable or to Maven command, e.g.
`mvn clean verify -Dhttp.proxyHost=HOST -Dhttp.proxyPort=PORT`.

## How to contribute

Fork repository, make changes, send us a pull request. We will review
your changes and apply them to the `master` branch shortly, provided
they don't violate our quality standards. To avoid frustration, before
sending us your pull request please run full Maven build:

```bash
$ mvn clean install -Pqulice
```

Keep in mind that JDK7 and Maven 3.1.0 are the lowest versions you may use.
