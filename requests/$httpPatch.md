# $httpPatch

`$httpPatch` sends a **PATCH request** to an API. Use this when you need to **partially update** an existing resource. Unlike PUT which replaces the whole thing, PATCH only changes the fields you send.

---

## Syntax

```
$httpPatch[Url;(Body)]
```

- `Url`: the web address of the API you are sending data to.
- `(Body)`: the data you want to send (usually JSON). This is **optional**, but most APIs expect at least `{}` if they require a body. Leave it fully empty only if the API explicitly accepts a bodyless request.

---

## What happens

1. `$httpPatch` sends your data to the URL.
2. The API finds the resource and updates only the fields you provided.
3. The response is stored in memory. Use [$httpResult](../responses/$httpResult.md) to see it.

---

## Example 1: Updating only the role

Change a user's role without touching their name or age:

```
$httpPatch[https://api.example.com/users/1;{"role":"admin"}]
$httpResult
```

What happens:

1. `$httpPatch` sends only the role to the API.
2. The API updates the user's role and leaves everything else unchanged.
3. `$httpResult` displays whatever the API returned.

To extract specific parts of the response, see the [$httpResult](../responses/$httpResult.md) page.

---

## Example 2: Updating multiple fields at once

Change a user's name and age at the same time:

```
$httpPatch[https://api.example.com/users/1;{"name":"Cenzo","age":25}]
$httpResult
```

What happens:

1. `$httpPatch` sends the name and age to the API.
2. The API updates only those two fields. Everything else stays the same.
3. `$httpResult` shows the response.

---

## Common uses

- **Changing a single setting** without resending everything
- **Updating a user's status or role** on a server
- **Fixing a typo** in a record
- **Saving partial form data** incrementally

---

## See also

- [$httpResult](../responses/$httpResult.md): to read the API's response
- [$httpStatus](../responses/$httpStatus.md): to check if the update succeeded
- [$httpAddHeader](../headers/$httpAddHeader.md): to set content type or send an API key
