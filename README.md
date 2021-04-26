# webworld

## Prerequisites

- Git - required for Heroku CLI
- [Heroku CLI](https://devcenter.heroku.com/articles/heroku-cli)
- Chocolatey (recommended for installing software on Windows)
- VS Code (recommended for code editing)
- Gradle (recommended)

```Powershell
choco install git -y
choco install tortoisegit -y
choco install heroku-cli -y
choco install gradle -y
choco upgrade all -y
refreshenv
```

## Java: Multiple Versions

Different versions of Java enable different features. You can install various Java Development Kits (JDK) via web site installers, or using chocolatey, or using your IDEs. 

## Install and Configue Java Versions in VS Code

VS Code makes it easy to:

1. Chose the Java version for this project.
2. Install additional JDK versions as desired.

To set this version, open VS Code. Hit CTRL SHIFT P (all 3 at the same time) to open the Command Palette, and type Java Configure Java Runtime to open this tab.

At the top of the Configure Java Runtime page, click "Installed JDKs" to see what's already avaiable.

If desired, scroll down to Install a JDK / AdoptOpenJDK and install 8, 11, 15 or all 3. I use the default Hotspot (recommended).

Scroll back up and click "Project JDK" to choose the version to use for this project.

## Java on Windows / Edit System Environment Variables

Windows wants to know what JDK to use by default. It's often safest to set this to JDK8 as that works with most projects. 

- Hit Windows Start key, type Edit the System Environment Variables / Open. 
- Click Environment Variables...
- Lower window / System Variables 
- Click Edit if JAVA_HOME exists or New if not 
- set JAVA_HOME to the location of your desired default, for example (one of the following)
  - C:\Program Files\OpenJDK\openjdk-8u282-b08
  - C:\Program Files\AdoptOpenJDK\jdk-15.0.2.7-hotspot
  - C:\Program Files\OpenJDK\jdk-16
- set path to include an entry with
  - %JAVA_HOME%\bin

IMPORTANT: Windows path must have NO MORE THAN ONE jdk bin folder in the path. Scan your system path AND your user path - remove all but %JAVA_HOME%\bin.

## Create a New Web App

Want to create a new one from scratch? 

Here's how this one was created.

- [Spring Initializr](https://start.spring.io/)
- Gradle Project
- Java
- Spring Boot (default version)
- Group: edu.nwmissouri.oop
- Artifact: webworld
- Packaging: Jar
- Java 11
- Dependency: Spring Web 

## Create a Favicon

Web apps should have a favicon to show in the browser tab.

- [favicon.io](https://favicon.io/favicon-generator/)
- Text: WW
- Font/Background Colors: #FFFFFF #006949
- Background: Circle
- Font Family: Chewy
- Font Size: 60

Download and extract to src\main\resources\static.

NOTE: Heroku requires an available favicon to run without error (or additional configuration).

## Commands (on Windows)

Create the local gradle wrapper and use it to build.

```Powershell
gradle wrapper
./gradlew build
```

After changes. Heroku app / deploy is configured to deploy on a push to GitHub.

```Powershell
./gradlew build
git add .
git commit -m "unique message here"
git push origin main
```

## Files for Java and Git

Java is a compiled language. 

- We write source code in .java files.
- The Java compiler compiles the code into .class files. 
- We bundle multiple files into .jar (Java archive files).
- We can execute a Java jar file by telling it the default class. 
- After editing source code, many artifacts are created. 
- We don't need all these generated artifacts in our project repo. 
- Anything we don't want to store in our central cloud repo, we add to a file named:
  - [.gitignore](./.gitignore)
- Java source files are kept in [src/main/java](./src/main/java)
- Addl code and other files are kept in [src/main/resources](./src/main/resources)

## Files for Gradle

We use Gradle (our chosen Java build tool) to  manage the paths, files, and commands needed to compile and run our project. 

Gradle requires the following files.

- [build.gradle](./build.gradle)
- [settings.gradle](./settings.gradle)

With Gradle installed on our machine, ```gradle wrapper``` creates:

- [gradlew](./gradlew)
- [gradlew.bat](./gradlew.bat)

Why? With Gradle Wrapper in our repo, others don't need to have Gradle installed locally - it comes for free with our project repo. :)

## Files for Heroku

We deploy our app to Heroku for free hosting in central location (so everyone can see it.)

Heroku requires the following files.

- [Procfile](./Procfile)
- [system.properties](./system.properties)

Read

- [Deploying Spring Boot Applications to Heroku
](https://devcenter.heroku.com/articles/deploying-spring-boot-apps-to-heroku)

Create Heroku app

```Powershell
heroku create
```