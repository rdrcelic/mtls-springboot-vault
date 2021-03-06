# Client in mTLS

This is simple client to demonstrate mTLS authentication. It is using Hashicorp Vault to store client keys.
To ease integration with Vault client is using [spring-cloud-starter-vault-config][1]

## Keystore management

Make sure client keystores are imported as Vault secret values (use provided script). In client code, user spring boot
property binding via @Value annotation. Since keystore values are Base64 encoded before storing in Vault, client has
to decode them. Also, since we have to provide path to _jks_ files, client is creating temporary files to configure SSL.

## Running end-to-end tests
By default end-to-end tests are not going to be executed in standard build pipeline. Spring boot is going to skip them
due to @IfProfileValue.
To execute end-to-end tests run tests with mvn test -Dtest-groups=e2e.

[1]: http://cloud.spring.io/spring-cloud-vault/
