# Connnection and Authentication

## Endpoint

The base API endpoint for opentodo is `https://api.opentodo.io`, unless you're accessing a self-deployed version.

HTTPS is always necessary, connections over HTTP will fail.

## Account

You have to create an account[TODO LINK], via the API, in order to access the API :|.

In the process, you will be prompted with the created account, which includes a secret key by default.

## Authentication

Opentodo uses `HTTP Basic`[https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization] schema for authentication, with your account's id being the username and one of your keys being the password.

Unless otherwise noted, every request to opentodo has to include an header like `Authorization: Basic <credential>`.

In which the `<credential>` is composed like this:

1. Combine your uid and token as `<account's id>:<a valid>` (`aladdin:opensesame`).
2. Encode the result via base64 (`YWxhZGRpbjpvcGVuc2VzYW1l`).
