# OIDC OP

## Usage

Configures a single OpenID Connect Provider in Airlock IAM.

It provides the following functionality (which can be extended or limited as per your requirements):
- Authorisation Code Grant Flow with optional support for PKCE (Proof Key for Code Exchange) and PAR (Pushed Authorization Request)
- Predefined standard scopes: email, profile
- ID Token, access token and refresh token
- Endpoints
  - OIDC Discovery
  - Token
  - User info
  - Revocation
  - Introspection
  - Dynamic Client Registration for persisted clients (for static clients see OIDC Static CLient snippet)

## Installation

1. Drag-and-drop the snippet onto the menu tree in the Airlock IAM Config Editor and import the snippet into your configuration.
2. In Loginapp, create a <code>OAuth 2.0/OIDC Authorization Servers</code> plugin if it does not yet exist.
3. In the drop-down box for Authorization Servers select <code>OAuth 2.0/OIDC Authorization Server - OIDC OP</code>.

## Required configuration

- In <code>OAuth 2.0/OIDC Authorization Server</code>
  - Specify identifier for new OIDC OP
  - Specify issuer id
- Create storage encryption key and copy the result
  ```
  openssl rand -base64 96 | tr -d '\n'
  ```
- Create external secrets
  |Name|Value|
  |----|-----|
  |<code>oidc op storage encryption</code>|output of openssl command above|
  |<code>op-signer-keystore</code>|any password you like|

- Create keystore for ID token signing (use the password set for <code>op-signer-keystore</code> above)
  ```
  cd instances/<instance-directory>
  mkdir oidc
  /opt/airlock-iam/jre/bin/keytool -genkeypair -keyalg RSA -keysize 2048 -keystore oidc/op-signer.jks -alias "airlock-iam-oidc-op"
  ```
- Click on <code>Errors</code> in the bottom menu

  ![Error Button](oidc-op-1.png "Error Button")
  - Provide links to the user context data items for <code>given_name</code>, <code>family_name</code>, and <code>email</code>.
  - Select the appropriate SQL data source for
    - OAuth 2.0 Pushed Authorization Request (PAR) Repository
    - OAuth 2.0 Session Repository
    - OAuth 2.0 Consent Repository
    - Technical Client Database Repositoy

## Next steps

Either, have clients register using DCR or create static client entries.