# $httpDelete

`$httpDelete` sends a **DELETE request** to an API. Use this when you need to **remove** a resource, like deleting a user, a message, or a record.

---

## Syntax

```
$httpDelete[Url;(Body)]
```

- `Url`: the web address of the API resource you want to delete.
- `(Body)`: data to include with the request (usually JSON). This is **optional**, but most APIs expect at least `{}` if they require a body. Leave it fully empty only if the API explicitly accepts a bodyless request.

---

## What happens

1. `$httpDelete` sends a request to the URL.
2. The API finds the resource and deletes it.
3. The response is stored in memory. Use [$httpResult](../responses/$httpResult.md) to see it.

---

## Example 1: Deleting a user

Remove a user from the database:

```
$httpDelete[https://api.example.com/users/1]
$httpResult
```

What happens:

1. `$httpDelete` tells the API to delete user 1.
2. The API removes the user and sends back a response (often a confirmation message).
3. `$httpResult` displays whatever the API returned.

To extract specific parts of the response, see the [$httpResult](../responses/$httpResult.md) page.

---

## Example 2: Delete with a body

Some APIs expect extra info with the delete request:

```
$httpDelete[https://api.example.com/users/1;{"reason":"inactivity"}]
$httpResult
```

What happens:

1. `$httpDelete` sends the delete request with a reason attached.
2. The API deletes the user and returns a response.
3. `$httpResult` shows the response.

---

## Common uses

- **Removing users or accounts** from a database
- **Cleaning up old records** like expired entries
- **Deleting messages or comments**
- **Unlinking or removing resources** from a server

---

## See also

- [$httpResult](../responses/$httpResult.md): to read the API's response
- [$httpStatus](../responses/$httpStatus.md): to check if the deletion succeeded
- [$httpAddHeader](../headers/$httpAddHeader.md): to send an API key or auth token
