# About the API

## Request formats

While making a **POST** or **PUT** request, use the following headers:

| Key | Value |
|---|---|
| Content-Type | application/json |

All the requests accept the body in JSON format. The responses are also encoded in JSON format.

> **Note:** The number of API requests is limited to 400 requests per 15 minutes. Kindly adhere to these limits. Crossing the specified limit would result in a *429 Too Many Requests* error.

## Response formats

The data returned from each method call would have one of the following fixed formats:

#### Success

```json
{
  "status": "success",
  "data": {}
}
```
The status part would always return `success` for each successful request which carries some data with it. Mostly, all successful requests would be returned with an **HTTP status code** of **200 OK**.

#### Error

```json
{
  "status": "error",
  "data": {}
}
```
The status part would always return `error` for each failed request which carries some error messages with it. The error requests are returned with an **HTTP status code** of **500 Internal Server Error** or **404 Not Found**.

#### Blank

The blank responses generally just contain the HTTP status code (mostly in the case of **204 Accepted** or **401 Unauthorized**) and no body
