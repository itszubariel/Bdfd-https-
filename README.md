# BDFD HTTP Guide

A beginner-friendly guide to the **`$http`** functions in BDFD.

---

## What this is about

The **`$http`** functions let your bot send and receive data over the internet. This is how your bot talks to other services.

The services your bot talks to are called **APIs**. Think of them as websites designed for bots instead of people. When you open a website in your browser, you see a page with text and images. When your bot talks to an API, it gets back raw data (usually JSON) that it can use directly.

There are different types of requests for different jobs:
- **GET**: read data from an API
- **POST**: send new data to an API
- **PUT**: replace existing data on an API
- **PATCH**: update part of existing data on an API
- **DELETE**: remove data from an API

Each type has its own function, and they all work the same way: you call the function, BDFD stores the response, then you use `$httpResult` to read it.

With these functions you can build:

- **AI chatbots**: talk to an AI API
- **Economy systems**: save and load user balances from a database
- **Weather commands**: get live weather data
- **Quote or joke commands**: pull content from public APIs
- **Custom databases**: connect your bot to your own backend

---

## How this guide is organized

Functions are grouped into three categories. Each category has its own folder, and each function has its own page.

**Requests**: making calls to APIs
- `$httpGet`, `$httpPost`, `$httpPut`, `$httpPatch`, `$httpDelete`

**Headers**: controlling what you send
- `$httpAddHeader`, `$httpRemoveHeader`, `$httpGetHeader`

**Responses**: reading what comes back
- `$httpResult`, `$httpStatus`

Every page explains:

- What the function does
- The exact **syntax** (how to write it)
- **What happens** when you call it
- One or two **simple examples** you can try
- **Common uses** for the function
- **Related functions** to check next

> Pick the function you need from the table below and click it.

---

## Functions

| Function | What it does |
|---|---|
| [$httpGet](requests/$httpGet.md) | Gets data from an API |
| [$httpPost](requests/$httpPost.md) | Sends data to an API |
| [$httpPut](requests/$httpPut.md) | Updates an existing resource on an API |
| [$httpPatch](requests/$httpPatch.md) | Partially updates an existing resource on an API |
| [$httpDelete](requests/$httpDelete.md) | Deletes a resource from an API |
| [$httpAddHeader](headers/$httpAddHeader.md) | Adds a custom header to your HTTP request |
| [$httpRemoveHeader](headers/$httpRemoveHeader.md) | Removes a header from your HTTP request |
| [$httpStatus](responses/$httpStatus.md) | Gets the HTTP status code of the response |
| [$httpResult](responses/$httpResult.md) | Gets the data returned by your HTTP request |
| [$httpGetHeader](headers/$httpGetHeader.md) | Gets a specific header from the response |

---

## Where to start

If you are **completely new** to HTTP functions, read these two in order:

1. **[$httpGet](requests/$httpGet.md)**: the simplest function. It just reads data.
2. **[$httpResult](responses/$httpResult.md)**: used right after `$httpGet` to see the data.

Once you understand those two, everything else will click into place.

---

## Source accuracy

> All syntax shown in this guide is checked against BDFD's **official wiki** and **official function list**.
