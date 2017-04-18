# Managing your homes

Each user can have multiple homes. The access and controls of all the homes are private to its owner.

A home is basically an object which is dependent on the user and it has 2 attributes - name and address.
* The **name** of the home would act as a label which can be used to identify multiple homes of a user.
* The **address** of the home would be a textual location which would be useful to show location information to the user, for example, while listing all the homes for a specific user.

This doc lists out all of the ways to manage homes.

> **Note:** Managing homes requires authentication. All of the CRUD operations for home management are available for both the developers and the naive users.

## Show all home data

To show the data of all the homes that belong to a user, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes |
| Method | GET |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

This yields the following response:
```json
{
  "status": "success",
  "data": []
}
```

## Show home data by home ID

To show the data of a specific home by its ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:id |
| Method | GET |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

This yields the following response (with sample data):

```json
{
  "status": "success",
  "data": []
}
```

If the home does not exist or if you don't have access to the home you are querying, then you get the following error with status code **404 Not Found**:
```json
{
  "status": "error",
  "data": {
    "message": "Home not found!"
  }
}
```

## Creating a home

To create a home, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes |
| Method | POST |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

and use the following body (sample values given):

```json
{
  "name": "White Mansion",
  "address": "123, ABCD Road, Imaginary City"
}
```

This yields the following response:
```json
{
  "status": "success",
  "data": {
    "id": 1,
    "name": "White Mansion",
    "address": "123, ABCD Road, Imaginary City",
    "user_id": 1
  }
}
```

## Changing an existing home's data

To change the data of an existing home by it's ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:id |
| Method | PUT |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

and use the following body (sample values given). Note that not all the keys are mandatory. It is recommended to put in only those keys that are to be changed:

```json
{
  "name": "Black Mansion"
}
```

This yields a **204 No Content** blank response, which indicates that the values have been changed. In case of an error, you would get a detailed error message in the specified error response format (refer to [About the API](01_about_the_api.md)).

## Deleting a home data

To delete an existing home by it's ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:id |
| Method | DELETE |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

This yields a **204 No Content** blank response, which indicates that the home has been deleted. In case of an error, you would get a detailed error message in the specified error response format (refer to [About the API](01_about_the_api.md)).
