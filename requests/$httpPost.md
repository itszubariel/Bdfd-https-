# $httpPost

`$httpPost` sends a **POST request** to an API. Use this when you need to **send data** to an API, like creating a new record or submitting a form.

---

## Syntax

```
$httpPost[Url;(Body)]
```

- `Url`: the web address of the API you are sending data to.
- `(Body)`: the data you want to send (usually JSON). This is **optional**, but most APIs expect at least `{}` if they require a body. Leave it fully empty only if the API explicitly accepts a bodyless request.

---

## What happens

1. `$httpPost` sends your data to the URL.
2. The API processes your data and usually creates something new.
3. The response is stored in memory. Use [$httpResult](../responses/$httpResult.md) to see it.

---

## Example 1: Sending data to create something

Create a new user by sending their info to the API:

```
$httpPost[https://api.example.com/users;{"name":"Cenzo","role":"user"}]
$httpResult
```

What happens:

1. `$httpPost` sends the user data to the API.
2. The API creates a new user and sends back a response (often with the new user's ID).
3. `$httpResult` displays whatever the API returned.

To extract specific parts of the response (like the new user's ID), see the [$httpResult](../responses/$httpResult.md) page.

---

## Example 2: POST with an empty body

Some APIs need a body but do not require specific data. Send `{}` as the body:

```
$httpPost[https://api.example.com/login;{}]
$httpResult
```

What happens:

1. `$httpPost` sends a POST request with an empty JSON object as the body.
2. The API processes it and returns a response.
3. `$httpResult` displays the response.

---

## Common uses

- **Creating new users or accounts** in a database
- **Submitting form data** like feedback or applications
- **Sending chat messages** to external services
- **Logging in or requesting tokens** from an auth API

---

## See also

- [$httpResult](../responses/$httpResult.md): to read the API's response
- [$httpStatus](../responses/$httpStatus.md): to check if the request worked
- [$httpAddHeader](../headers/$httpAddHeader.md): to set content type or send an API key
