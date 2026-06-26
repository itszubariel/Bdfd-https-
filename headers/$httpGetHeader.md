# $httpGetHeader

`$httpGetHeader` retrieves the value of a specific header from the last HTTP response. Use this when you need to read response headers like `content-type`, `rate-limit`, or a custom header set by the API.

---

## Syntax

```
$httpGetHeader[Header Key]
```

- `Header Key`: the name of the header you want to read (e.g. `content-type`, `x-ratelimit-remaining`).

---

## What happens

1. You make an HTTP request with `$httpGet`, `$httpPost`, or another HTTP function.
2. The API sends back a response with headers.
3. `$httpGetHeader` looks up the header you asked for and returns its value.

---

## Example 1: Reading the content type

```
$httpGet[https://api.example.com/users/1]
$httpGetHeader[content-type]
```

If the API returns `content-type: application/json`, the output is `application/json`.

---

## Example 2: Checking rate limit info

Many APIs tell you how many requests you have left using headers:

```
$httpGet[https://api.example.com/users/1]
$httpGetHeader[x-ratelimit-remaining]
```

What happens:

1. `$httpGet` requests the user.
2. The API includes a `x-ratelimit-remaining` header in its response.
3. `$httpGetHeader` returns that value so your bot knows how many requests are left.

---

## Common uses

- **Checking rate limits** to avoid being blocked by an API
- **Reading the content type** of the response
- **Extracting custom headers** that an API uses to send extra info

---

## See also

- [$httpAddHeader]($httpAddHeader.md): to add a header to your request
- [$httpRemoveHeader]($httpRemoveHeader.md): to remove a header from your request
- [$httpStatus](../responses/$httpStatus.md): to check if the request succeeded
