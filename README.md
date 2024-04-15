# Spring Web Application with Authorization Code Flow with PKCE

This is a simple Spring Boot web application with just a secured index page at the `/` location, and a profile page at `/profile`, built with Thymeleaf templates, for the purpose of demonstrating the OpenID Connect Authorization Code Flow with PKCE, using Auth0 as the identity provider.

## Prerequisites

- [Java OpenJDK 17](https://jdk.java.net/java-se-ri/17)
- [Auth0 account](https://auth0.com/signup)
- [Auth0 CLI 1.4.0](https://github.com/auth0/auth0-cli#installation)


## Installation

Clone the repository:

```shell
git clone https://github.com/indiepopart/spring-web-pkce.git
```

## Register the Application as Regular Web App in Auth0

Sign up at [Auth0](https://auth0.com/signup) and install the [Auth0 CLI](https://github.com/auth0/auth0-cli). Then in the command line run:

```shell
auth0 login
```

The command output will display a device confirmation code and open a browser session to activate the device.

Using the Auth0 CLI, register the web application as an authentication client for Auht0:

```shell
auth0 apps create \
  --name "Spring MVC" \
  --description "Spring Boot Webapp" \
  --type regular \
  --callbacks http://localhost:8080/login/oauth2/code/okta \
  --logout-urls http://localhost:8080 \
  --reveal-secrets
```

Copy `application.yml.example` to `application.yml` and fill in the values with your Auth0 client settings.

```yml
okta:
  oauth2:
    issuer: https://<your-auth0-domain>/
    client-id: <client-id>
    client-secret: <client-secret>
    post-logout-redirect-uri: http://localhost:8080
```

## Run the application

```shell
./gradlew bootRun
```

In your browser, open a private window and navigate to [http://localhost:8080](http://localhost:8080). You will be redirected to the Auth0 Universal Login page.