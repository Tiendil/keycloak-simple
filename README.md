
# Customized Keycloak

Customized Keycloak docker container for my personal projects.

## Features / Changes

- Pre-installed [Magic Link extension](https://github.com/p2-inc/keycloak-magic-link)
- Pre-installed [Tailclokify theme](https://github.com/ALMiG-Kompressoren-GmbH/tailcloakify)
- Pre-installed [Fedds Fun theme](https://github.com/Tiendil/feeds-fun-tailcloakify/tree/feeds-fun-changes)
- Intended for magic link login + social login only (no password login). Both flows create users on first login. Both flows merge users if the same email is used.

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


- TODO: add an instruction to configure local domain names
- TODO: index page with links to test urls
- TODO: instruction on configuring social login
- TODO: join configuration
- "Browser" flow is replaced with "Simple browser" flow.
- "First broker login" flow is replaced with "Simple first broker login.
- TODO: some changes listed here are not an actual changes, but dev setup (like flows changes). Need to clarify that.
- TODO: add notes on configuration of tailcloak
- TODO: specify dev user creds
- "first name" and "last name" no longer required fields (Removed)
- resetPasswordAllowed: false — no passwords — no resets
- registrationEmailAsUsername: true
- TODO: hide registration form & link to it from the login page
- TODO: apple social login
- TODO: start keycloak in optimized mode

## Simple browser flow

The flow provides two ways to authenticate:

1. Via magic link sent to the user's email.
2. Via social login (if configured).

TODO: what with creation user on first login
TODO: what with merging users

# Instruction

1. Before sending emails, set SMPT user_id/password in the Keycloak admin console.
