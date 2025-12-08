FROM quay.io/keycloak/keycloak:26.4.2 AS builder

ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=false

# TODO: we may want to parameterize this in the future
ENV KC_DB=postgres

# TODO: we may want to enable/disable keycloak features here

WORKDIR /opt/keycloak

ADD --chown=keycloak:keycloak \
    --chmod=644 \
    ./docker/keycloak/magic-link/keycloak-magic-link-0.52.jar \
    ./providers/

ADD --chown=keycloak:keycloak \
    --chmod=644 \
    ./docker/keycloak/tailcloakify/tailcloakify-theme-1.2.0.jar \
    ./providers/

RUN ./bin/kc.sh build

FROM quay.io/keycloak/keycloak:26.4.2
COPY --from=builder /opt/keycloak/ /opt/keycloak/
