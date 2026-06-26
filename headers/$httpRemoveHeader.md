# $httpRemoveHeader

`$httpRemoveHeader` removes a header that was previously added with `$httpAddHeader`. Use this when you need to clear a header before your next request.

---

## Syntax

```
$httpRemoveHeader[Header name]
```

- `Header name`: the name of the header to remove.

---

## What happens

1. `$httpRemoveHeader` removes the header from memory.
2. The next HTTP function you call will **not** include that header.

---

## Example 1: Removing a header before the next request

```
$httpAddHeader[Authorization;Bearer abc123def]
$httpGet[https://api.example.com/protected]
$httpResult

$httpRemoveHeader[Authorization]
$httpGet[https://api.example.com/public]
$httpResult
```

What happens:

1. The first request sends the `Authorization` header and gets protected data.
2. `$httpRemoveHeader` clears the `Authorization` header.
3. The second request does **not** include the header. The public endpoint works fine without it.

---

## Example 2: Resetting headers between requests

```
$httpAddHeader[content-type;application/json]
$httpPost[https://api.example.com/data;{"key":"value"}]
$httpResult

$httpRemoveHeader[content-type]
$httpPost[https://api.example.com/login]
$httpResult
```

What happens:

1. The first request sends JSON with the correct content type.
2. `$httpRemoveHeader` clears it before the next request.
3. The second request sends no content type header.

---

## Common uses

- **Clearing authentication headers** after accessing a protected endpoint
- **Resetting headers** between requests to avoid sending stale data
- **Removing headers** that are no longer needed

---

## See also

- [$httpAddHeader]($httpAddHeader.md): to add a header to your request
- [$httpGetHeader]($httpGetHeader.md): to read a header from the response
- [$httpResult](../responses/$httpResult.md): to read the data from the response
