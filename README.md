# Node SAML (fork)

This is a fork of the [original](https://github.com/node-saml/node-saml) SAML 2.0 authentication provider for Node.js.

## Purpose

Upon testing SAML authentication, I set up [Keycloak](https://www.keycloak.org/) to encrypt the assertions, but I chose not to sign them.

node-saml fails with `Error: Invalid signature from encrypted assertion` as it assumes the encrypted SAMLAssertion must be signed as well.
    
While allowing such scenario in production environments could be considered a security risk, node-saml should have a flag to respect the IdP's decision to send unsigned encrypted assertions.

## Changes

This fork adds the following configuration property to the constructor:

- `allowUnsignedEncryptedAssertions`: when `true`, bypasses signature validation when a SAMLAssertion is both encrypted and unsigned (defaults to `false`)

## Installation

```shell
npm install @montblanc0/node-saml
```

For more instructions, please refer to the [official README](https://github.com/node-saml/node-saml/blob/master/README.md).