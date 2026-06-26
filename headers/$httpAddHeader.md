# $httpAddHeader

`$httpAddHeader` adds a **custom header** to your next HTTP request. Use this when an API needs extra information like an API key, content type, or authentication token.

---

## Syntax

```
$httpAddHeader[Header name;Value]
```

- `Header name`: the name of the header (e.g. `content-type`, `Authorization`).
- `Value`: the value of the header (e.g. `application/json`, `Bearer mytoken`).

---

## What happens

1. `$httpAddHeader` stores the header in memory.
2. The next HTTP function you call (`$httpGet`, `$httpPost`, etc.) includes that header in its request.
3. The header is only used once. You must call `$httpAddHeader` again before each request that needs it.

---

## Example 1: Sending an API key

```
$httpAddHeader[Authorization;Bearer abc123def]
$httpGet[https://api.example.com/users/1]
$httpResult
```

What happens:

1. `$httpAddHeader` sets the `Authorization` header to `Bearer abc123def`.
2. `$httpGet` sends the request with that header included.
3. The API sees the valid token and returns the user data.
4. `$httpResult` displays the response.

---

## Example 2: Setting content type

Tell the API you are sending JSON data:

```
$httpAddHeader[content-type;application/json]
$httpPost[https://api.example.com/users;{"name":"Cenzo","role":"admin","age":25}]
$httpResult
```

What happens:

1. `$httpAddHeader` sets the content type to JSON.
2. `$httpPost` sends the data with the correct content type header.
3. The API knows to read the body as JSON.
4. `$httpResult` shows the response.

---

## Common uses

- **Sending API keys or tokens** for authenticated requests
- **Setting the content type** of data you are sending
- **Specifying custom headers** required by a particular API

---

## See also

- [$httpRemoveHeader]($httpRemoveHeader.md): to remove a header before the next request
- [$httpGetHeader]($httpGetHeader.md): to read a header from the response
- [$httpStatus](../responses/$httpStatus.md): to check if the request succeeded
