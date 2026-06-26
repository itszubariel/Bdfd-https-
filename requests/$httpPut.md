# $httpPut

`$httpPut` sends a **PUT request** to an API. Use this when you need to **replace** an existing resource with new data. PUT is commonly used to update records like users, settings, or items.

---

## Syntax

```
$httpPut[Url;(Body)]
```

- `Url`: the web address of the API you are sending data to.
- `(Body)`: the data you want to send (usually JSON). This is **optional**, but most APIs expect at least `{}` if they require a body. Leave it fully empty only if the API explicitly accepts a bodyless request.

---

## What happens

1. `$httpPut` sends your data to the URL.
2. The API finds the resource and replaces it with your new data.
3. The response is stored in memory. Use [$httpResult](../responses/$httpResult.md) to see it.

---

## Example 1: Updating a user

Replace an existing user's info with new data:

```
$httpPut[https://api.example.com/users/1;{"name":"Cenzo","role":"admin","age":25}]
$httpResult
```

What happens:

1. `$httpPut` sends the new user data to the API.
2. The API finds user 1 and replaces their old data with the new data.
3. `$httpResult` displays whatever the API returned (often the updated record).

To extract specific parts of the response (like the updated user's name), see the [$httpResult](../responses/$httpResult.md) page.

---

## Example 2: Updating settings

Replace a server's settings with a new config:

```
$httpPut[https://api.example.com/settings/1;{"theme":"dark","language":"en"}]
$httpResult
```

What happens:

1. `$httpPut` sends the new settings to the API.
2. The API replaces the old settings with the new ones.
3. `$httpResult` shows the response.

---

## Common uses

- **Updating user profiles** with new information
- **Replacing configuration settings** on a server
- **Overwriting existing records** in a database
- **Syncing data** between your bot and an external service

---

## See also

- [$httpResult](../responses/$httpResult.md): to read the API's response
- [$httpStatus](../responses/$httpStatus.md): to check if the update succeeded
- [$httpAddHeader](../headers/$httpAddHeader.md): to set content type or send an API key
