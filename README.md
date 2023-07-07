# verdaccio-oidc-ui

## About

This plugin integrates with Verdaccio and re-exposes a new authentication plugin API that makes authentication more extensible and combinable, including suppport for modications to the default UI.

The result is a more consistent login experience and support for long-requested authentication features, such as: configurable setup instructions, multiple authentication methods, fine-grained permissions, reverse proxy authentication, 2FA, WebAuthn, and more.

This is a Verdaccio plugin that offers OIDC OAuth integration for both the browser and the command line.

### Compatibility

- Verdaccio 5
- Node 14, 16
- Chrome, Firefox, Firefox ESR, Edge, Safari

If you would like to use this with Verdaccio 3-4, Node.js 10-13, or IE you can use version 2 of the plugin.

## Setup

### Install

```sh
git clone https://github.com/kuoruan/verdaccio-oidc-ui.git /path/of/verdaccio-oidc-ui
npm install && npm run build
cd /path/of/verdaccio
npm install /path/of/verdaccio-oidc-ui
```

### Verdaccio Config

Merge the below options with your existing Verdaccio config:

```yml
middlewares:
  oidc-ui:
    enabled: true

auth:
  oidc-ui:
    configuration-endpoint: https://example.com/.well-known/openid-configuration
    # issuer: https://example.com
    # authorization-endpoint: https://example.com/oauth/authorize
    # token-endpoint: https://example.com/oauth/token
    # userinfo-endpoint: https://example.com/oauth/userinfo
    # jwks-uri: https://example.com/oauth/jwks
    # scope: openid email groups # optional. custom scope
    username-claim: name
    groups-claim: groups # optional. claim to get groups from
    client-id: CLIENT_ID
    client-secret: CLIENT_SECRET
    authorized-group: false # false to disable login group filter
    # group-users:
    #   animal:
    #     - tom
    #     - jack # optional. custom the group users. eg. animal group has user tom and jack
    # provider-type: gitlab # define this to get groups from gitlab api
```