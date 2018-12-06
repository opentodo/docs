# Accounts

TODO

## Account object

attribute | detail
--- | ---
id | uuid as string
keys | an array of keys [TODO]

## Relations

An `account` has many `key`s.

## Create an account

Creates a new account.

The created account contains one `key` in the field `keys`. **The key will only be revealed once**.

> request: POST /accounts

```shell
curl https://api.opentodo.io/accounts \
  -u 

# or use -H directly

curl "api_endpoint_here"
  -H "Authorization: meowmeowmeow"
```
> response

```json
{
  
}
```
