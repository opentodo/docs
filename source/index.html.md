---
title: open-todo API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='https://opentodo.io'>opentodo.io</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

# includes:
#   - errors

search: true
---

# Introduction

open-todo is an open-sourced platform focus on managing tasks conveniently, productively, and intelligently.

The current version of open-todo API is RESTful, meaning resource-oriented endpointes and respecting HTTP headers, status codes, verbs etc.

<aside class="notice">
open-todo is still in alpha phase.
</aside>

# Endpoint

The open-todo API endpoints is: `https://api.opentodo.io/`

<aside class="notice">HTTPS is essential.</aside>

# Authentication

## Account and Token

To access the open-todo API, you have to go create an account at [opentodo.io/account](https://opentodo.io/account), an `uid` and some `token`s will be assigned to you, which will be used for authentication.

<aside class="notice">
When creating an open-todo Account, we currently support sign in with Google. We will support more methods later.
</aside>

## Authentication with Header

Opentodo use `Basic authenticate scheme`. Unless otherwise noted, every request to open-todo have to include an header like `Authorization: Basic <credential>`.

In which the `<credential>` is composed like this:

1. Combine your uid and token as "uid:token" (`aladdin:opensesame`).
2. Encode the result via base64 (`YWxhZGRpbjpvcGVuc2VzYW1l`).

<aside class="notice">
For historical reasons, there maybe some newlines (<code>\n</code>) included in the result of default base64 encoding method.
You should use methods like <code>urlsafe_encode64</code>, <code>Base64.encodeBase64URLSafe</code> to get rid <code>\n</code>s in result.
</aside>

<aside class="notice">
Learn more about HTTP Basic authenticate scheme at <a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization">here</a>.
</aside>

# Users

`user` is a core concept in open-todo, which represents an, well, user.

# Tasks

`task` is a core concept in open-todo, which represents an one-time or recurrent work to be done.

## Data model

### Attributes

attribute | detail
--- | ---
name | name
due_time | timestamp

### Associations

- One `task` belongs to an `user`.

## Create a Task

### Endpoint

`POST https://api.opentodo.io/tasks`

### Body

```json
{
	"task": {
		"name": "taskname",
		"due_time": "2017-12-02 13:23"
	}
}
```

### Response

```json
{
    "id": "bf87da07-8cca-4008-9bd9-ac587627fc8b",
    "name": "taskname",
    "due_time": "2017-12-02T13:23:00.000Z",
    "created_at": "2017-12-20T10:25:35.134Z"
}
```

## List Tasks of Current User

```javascript
TODO
```

> TODO:

```json
[
  'TODO'
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET https://api.opentodo.io/tasks`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Task

```javascript
let response = fetch('')
```

> The above command returns JSON structured like this:

```json
{
  "id": "some-uuid",
  "name": "Max",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">Inside HTML code blocks like this one, you can't use Markdown, so use <code>&lt;code&gt;</code> blocks to denote code.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the kitten to retrieve

# Smart Tasks

