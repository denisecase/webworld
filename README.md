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

## Create a Web App

- [Spring Initializr](https://start.spring.io/)
- Gradle Project
- Java
- Spring Boot (default version)
- Group: edu.nwmissouri.oop
- Artifact: webworld
- Packaging: Jar
- Java 11
- Dependency: Spring Web 

## Commands (on Windows)

```Powershell
gradle build
gradle wrapper
./gradlew build
./gradlew build deployHeroku
```

## Deploy free with Heroku

Heroku requires:

- Procfile
- system.properties

Read

- [Deploying Spring Boot Applications to Heroku
](https://devcenter.heroku.com/articles/deploying-spring-boot-apps-to-heroku)

Create Heroku app

```Powershell
heroku create
```