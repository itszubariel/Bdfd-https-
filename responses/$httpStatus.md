# $httpStatus

`$httpStatus` returns the **HTTP status code** from your last HTTP request. Use this to check whether the request succeeded, failed, or something else happened.

---

## Syntax

```
$httpStatus
```

Takes no arguments. Place it right after `$httpGet`, `$httpPost`, or any other HTTP function.

---

## What happens

HTTP status codes are three-digit numbers. The most common ones are:

| Code | Meaning |
|:---:|:---|
| 200 | OK: the request succeeded |
| 201 | Created: a new resource was created |
| 400 | Bad Request: the API did not understand the request |
| 401 | Unauthorized: the API key is missing or wrong |
| 403 | Forbidden: you do not have permission |
| 404 | Not Found: the resource does not exist |
| 500 | Internal Server Error: something went wrong on the API's side |

---

## Example 1: Checking if a request worked

```
$httpGet[https://api.example.com/users/1]
$httpStatus
```

If the user exists, this returns `200`. If the user does not exist, this returns `404`.

---

## Example 2: Using status in a condition

```
$httpGet[https://api.example.com/users/1]
$if[$httpStatus==200]
  User found!
$else
  User not found.
$endif
```

What happens:

1. `$httpGet` requests the user.
2. `$httpStatus` is compared to `200`.
3. If they match, the bot says "User found!".
4. If not, the bot says "User not found."

---

## Common uses

- **Validating that a request worked** before reading the result
- **Error handling** in commands that rely on external APIs
- **Debugging** when an API request returns unexpected results

---

## See also

- [$httpResult]($httpResult.md): to read the data from the response
- [$httpGet](../requests/$httpGet.md): to make a GET request
- [$httpAddHeader](../headers/$httpAddHeader.md): to send an API key for authenticated requests
