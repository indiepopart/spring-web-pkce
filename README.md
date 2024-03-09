# Spring Web Application with Authorization Code Flow with PKCE

This is a basic web application with just a secured index page at the '/' location.


Clone the repository:

```shell
git clone 

Copy `.env.example` to `.env` and fill in the values with your Auth0 client settings.

## Register the Application as Regular Web App

```shell
auth0 apps create \
  --name "Spring MVC" \
  --description "Spring Boot Webapp" \
  --type spa \
  --callbacks http://localhost:4040/login/oauth2/code/okta \
  --logout-urls http://localhost:4040 \
  --reveal-secrets
```

