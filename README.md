# Hacking the Internet of Things

## NetHome
NetHome is a **Home Appliances as a Service** based on the **Internet of Things** which intends to connect various types of home appliances under one control system, allowing seamless remote control, automation and maintenance of all kinds of devices.

NetHome has easy-to-use **JSON APIs**. All of the APIs are documented here.

### About the API

An API (Application programming interface) is a protocol intended to be used as an interface by software components to communicate with each other.

Our API supports many methods, so there should not be a problem coding some nice applications.

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

The blank responses generally just contain the HTTP status code (mostly in the case of **204 Accepted** or **403 Forbidden**) and no body

#### Other notes

While making a **POST** or **PUT** request, use the following headers:

| Key | Value |
|---|---|
| Content-Type | application/json |

All the requests accept the body in JSON format. The responses are also encoded in JSON format.

### Authentication

#### Developer registration

1. Go to [the event registration page](https://www.thecollegefever.com/) and register yourself.

2. Post registration, your account would be activated within 24 hours. You will get an email with your registration details once your account is activated.

3. Once you get your login details, you can start using the platform. There is no limit on the number of requests or the amount of data that you produce while using the platform.

4. Creating and editing user details have been disabled for security purposes. You can only use the login feature as of now.

### Login

For the login procedure, use the following endpoint:

**Method:** POST  
**Headers:**
Content-Type: *application/json*  
**Body:**
```json
{
  "username": "...",
  "password": "..."
}
```
You can use either email or username to log in. Using both of them at once would throw an error.

This yields the following response:
```json
{
  "status": "success",
  "data": {
    "token": "..."
  }
}
```
The token is a [JWT](https://jwt.io/) token which is a key that identifies a particular user. All the other request that require authentication should have this token in the request header. The format of the header would be:

| Key | Value |
|---|---|
| Content-Type | application/json |
| Authorization | JWT *your_token* |

Failing to put this on the header would result in a **403 Unauthorized** error.
