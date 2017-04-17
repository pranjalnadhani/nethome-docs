### Authentication

#### Registration

For registering a naive user account, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/register |
| Method | POST |
| Headers | Content-Type: *application/json* |

and use the following body (sample values given):

```json
{
  "username": "nethome_fan",
  "email": "nethome.fan@gmail.com",
  "password": "password",
  "mobile_no": 9876543210
}
```

This yields the following response:
```json
{
  "status": "success",
  "data": {
    "role": "naive",
    "id": 1,
    "username": "nethome_fan",
    "email": "nethome.fan@gmail.com",
    "mobile_no": "9876543210"
  }
}
```

#### Developer registration

To be able to access some of the high authority API features, you would need a developer account. Also, a developer account is necessary for participating in the competition. Thus, to get an account, follow these steps:

1. Go to [the event registration page](https://www.thecollegefever.com/events/hacking-the-iot) and register yourself.

2. Post registration, your account would be activated within 24 hours. You will get an email with your registration details once your account is activated.

3. Once you get your login details, you can start using the platform.

### Login

For the login procedure, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/login |
| Method | POST |
| Headers | Content-Type: *application/json* |

and use the following body (sample values given):

```json
{
  "username": "nethome_fan",
  "password": "password"
}
```
You can use either email or username to log in. Using both of them at once would throw an error.

This yields the following response:
```json
{
  "status": "success",
  "data": {
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJpZCI6MX0.4XOtShiTei_JuP0nakNtFeBBKbmi_eUcCuQOAui-iaQ"
  }
}
```
The token is a [JWT](https://jwt.io/) token which is a key that identifies a particular user. All the other request that require authentication should have this token in the request header. The format of the header would be:

| Key | Value |
|---|---|
| Content-Type | application/json |
| Authorization | JWT *your_token* |

Failing to put this on the header would result in a **401 Unauthorized** error.
