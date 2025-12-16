
# Customized Keycloak

Customized Keycloak docker container for my personal projects.

## Features / Changes

### Extentions

- Pre-installed [Magic Link extension](https://github.com/p2-inc/keycloak-magic-link)
- Pre-installed [Tailclokify theme](https://github.com/ALMiG-Kompressoren-GmbH/tailcloakify)
- Pre-installed [Fedds Fun theme](https://github.com/Tiendil/feeds-fun-tailcloakify/tree/feeds-fun-changes)

### Flows

- This setup is intended for magic link login + social login only (no password login).
- Both flows create users on first login.
- Both flows merge users if the same email is used.

### Infrastructure

Check [docker-compose.yml](./docker-compose.yml) and [./docker](./docker) folder for details.

- Keycloak as the Identity Provider (IdP).
- Caddy as reverse proxy for all services with automatic HTTPS using Let's Encrypt.
- OAuth2-proxy in front of Keycloak to handle OAuth2/OIDC flows.
- PostgreSQL as the database for Keycloak.

## Usage

Add `keycloak.local` and `idp.keycloak.local` to your `/etc/hosts` file:

```
127.0.0.1 keycloak.local
127.0.0.1 idp.keycloak.local
```

Build keycloak image:

```bash
docker compose build keycloak
```

Run services:

```bash
docker compose up
```

Open https://keycloak.local in your browser. You'll see the page with links to test Keycloak login flows.

**Note:** Keycloak may need an additional configuration step.

## Keycloak Configuration

By default, this Keycloak comes with two realms:

- `master` — the default Keycloak admin realm, admin user/pass: `admin`/`admin`.
- `dev` — the development realm that we are going to use.

What you may want to configure/change in the `dev` realm:

- SMTP settings for sending emails.
- Social login providers (e.g., Google, GitHub, etc.) if needed.

What is already configured in the `dev` realm:

- Removed  "first name" and "last name" profile fields.
- Login with email allowed.
- Emails is equal to the username.
- Registration is disabled. Login form works like registration form.
- Reset password is disabled — there are no passwords.

## TODO

- Add extension for the apple social login.
