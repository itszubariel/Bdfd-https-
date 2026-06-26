# $httpGet

`$httpGet` sends a **GET request** to an API. Use this when you only need to **read** data. GET requests are the most common type of HTTP request.

---

## Syntax

```
$httpGet[Url]
```

- `Url`: the web address of the API you want to get data from.

---

## What happens

1. `$httpGet` sends a request to the URL you give it.
2. The API processes the request and sends data back.
3. The response is stored in memory. Use [$httpResult](../responses/$httpResult.md) to see it.

---

## Example 1: Basic GET request

Fetch a random quote from a quotes API:

```
$httpGet[https://api.example.com/quotes/random]
$httpResult
```

What happens:

1. `$httpGet` requests a random quote from the API.
2. The API returns the quote data.
3. `$httpResult` displays whatever came back.

To extract specific parts of the response (like the quote text or author name), see the [$httpResult](../responses/$httpResult.md) page.

---

## Example 2: GET with a specific resource

Some APIs let you request a specific item by including its ID in the URL:

```
$httpGet[https://api.example.com/users/1]
$httpResult
```

What happens:

1. `$httpGet` requests the user with ID 1.
2. The API returns that user's data.
3. `$httpResult` shows the full response.

---

## Common uses

- **Fetching quotes, jokes, or facts** from public APIs
- **Getting user data** from a database API
- **Checking weather or server status**
- **Reading lists of items**, like shop inventory or leaderboard scores

---

## See also

- [$httpResult](../responses/$httpResult.md): to read the data that came back
- [$httpStatus](../responses/$httpStatus.md): to check if the request succeeded
- [$httpAddHeader](../headers/$httpAddHeader.md): to send an API key or other header
