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

## Create a Favicon

Web apps should have a favicon to show in the browser tab.

- [favicon.io](https://favicon.io/favicon-generator/)
- Text: WW
- Font/Background Colors: #FFFFFF #006949
- Background: Circle
- Font Family: Chewy
- Font Size: 60

Download and extract to src\main\resources\static.


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