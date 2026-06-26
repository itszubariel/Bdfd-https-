# $httpResult

`$httpResult` retrieves the data returned by your last HTTP request. You call this right after `$httpGet`, `$httpPost`, or any other HTTP function to actually **see** or **use** what the API sent back.

---

## Syntax

`$httpResult` has two forms.

**Form 1: get everything as plain text**

```
$httpResult
```

Returns the entire response as raw text. Use this when the API returns a simple string or when you just want to see the full response.

**Form 2: extract a specific value from JSON**

```
$httpResult[key;...]
```

- `key`: one or more keys that point to the value you want. Each key navigates one level deeper into the JSON.

Use this when the API returns JSON and you only need one piece of it.

---

## Form 1: Getting everything

The simplest way to use `$httpResult` is with **no arguments**. This returns the entire response.

### Example

```
$httpGet[https://api.example.com/user]
$httpResult
```

If the API returns:

```json
{"name":"Cenzo","role":"admin","age":25}
```

Then `$httpResult` would output:

```
{"name":"Cenzo","role":"admin","age":25}
```

That is useful for testing, but most of the time you only want one value, like the `name`.

---

## Form 2: Extracting from JSON

When an API returns JSON, you can drill down to the exact value you need using `$httpResult[Key1;Key2;...]`.

### Understanding JSON structure

JSON is made of three things:

- **Objects**: wrapped in `{}`, contain keys and values.
- **Arrays**: wrapped in `[]`, contain items you access by index number.
- **Values**: strings, numbers, booleans, or null.

To extract a value, you follow the path from the top level down to the value you want.

---

### Example 1: Simple object

The API at `https://api.example.com/user` returns this JSON:

```
{
  "name": "Cenzo",
  "role": "admin",
  "age": 25
}
```

To get the `name`:

```
$httpResult[name]
```

The path is:

```
$httpResult
     |
    name
     |
  "Cenzo"
```

To get the `role`:

```
$httpResult[role]
```

The path is:

```
$httpResult
     |
    role
     |
  "admin"
```

---

### Example 2: Nested object

The API at `https://api.example.com/user/profile` returns this JSON:

```
{
  "user": {
    "name": "Cenzo",
    "details": {
      "role": "admin",
      "age": 25
    }
  }
}
```

To get the `role` inside `details` inside `user`:

```
$httpResult[user;details;role]
```

The path is:

```
$httpResult
     |
    user
     |
   details
     |
    role
     |
  "admin"
```

Each semicolon moves one level deeper.

---

### Example 3: Array with an object

The API at `https://api.example.com/search` returns this JSON:

```
{
  "results": [
    {
      "url": "https://example.com/image.png",
      "name": "Cenzo"
    }
  ]
}
```

To get the `url` from the first item in the `results` array:

```
$httpResult[results;0;url]
```

- `results`: go into the `results` key (which is an array).
- `0`: take the first item in the array (index 0).
- `url`: get the `url` key from that item.

The path looks like this:

```
$httpResult
     |
   results  (this is an array)
     |
      ↓
   [ 0 ]    (first item in the array)
     |
    url
     |
  "https://example.com/image.png"
```

---

### Example 4: Array with multiple items

The API at `https://api.example.com/items` returns this JSON:

```
{
  "results": [
    {"name": "Cenzo",  "url": "https://example.com/001.png"},
    {"name": "Zub",   "url": "https://example.com/002.png"},
    {"name": "Uncle",  "url": "https://example.com/003.png"}
  ]
}
```

To get the `name` of the second item:

```
$httpResult[results;1;name]
```

- `results`: go into the `results` array.
- `1`: take the second item (index 1).
- `name`: get the `name` key.

The path:

```
$httpResult
     |
   results
     |
   [ 1 ]    (second item: {"name": "Zub", "url": "..."})
     |
    name
     |
   "Zub"
```

Array indexes always start at `0`. So `0` is the first item, `1` is the second, `2` is the third, and so on.

---

### Example 5: Deeply nested data

The API at `https://api.example.com/posts` returns this JSON:

```
{
  "data": {
    "posts": [
      {
        "id": 1,
        "content": "Hello",
        "author": {
          "username": "Cenzo",
          "avatar": "https://example.com/avatar.png"
        }
      },
      {
        "id": 2,
        "content": "World",
        "author": {
          "username": "Zub",
          "avatar": "https://example.com/avatar2.png"
        }
      }
    ]
  }
}
```

To get the avatar of the first post's author:

```
$httpResult[data;posts;0;author;avatar]
```

The path:

```
$httpResult
     |
    data
     |
   posts
     |
   [ 0 ]       (first post)
     |
   author
     |
   avatar
     |
  "https://example.com/avatar.png"
```

To get the content of the second post:

```
$httpResult[data;posts;1;content]
```

The path:

```
$httpResult
     |
    data
     |
   posts
     |
      ↓
   [ 1 ]       (second post)
     |
   content
     |
   "World"
```

---

## Summary

- Use `$httpResult` alone to see the full response.
- Use `$httpResult[key1;key2;...]` to extract a specific value.
- Object keys are used as-is: `user`, `name`, `url`.
- Array items are accessed by index, starting at `0`.
- Separate each step with a semicolon.
- Each semicolon goes one level deeper into the JSON.

---

## Common uses

- **Displaying a single value** from an API response (like a quote, username, or score)
- **Extracting data from nested JSON** when the API returns complex structures
- **Getting specific items from arrays** (like the first result or the top player)
- **Using parts of the response** in embeds, messages, or variables

---

## See also

- [$httpStatus]($httpStatus.md): to check if the request worked before reading the result
