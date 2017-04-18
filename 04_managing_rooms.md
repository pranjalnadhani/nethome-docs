# Managing your rooms

Each home can have multiple rooms. The access and controls of all the rooms are private to its owner.

A room is basically an object which is dependent on a particular home and it has a single attribute - name.
* The **name** of the room would act as a label which can be used to identify multiple rooms of a home.
This doc lists out all of the ways to manage rooms.

> **Note:** Managing rooms requires authentication. All of the CRUD operations for room management are available for both the developers and the naive users.

> Since rooms are dependent on homes, a home should be created first, and it's reference must be passed along with each URL shown below. To create a home, refer to [Managing Homes](03_managing_homes)

## Show all room data

To show the data of all the rooms that belong to a home (identified by it's ID), use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:home_id/rooms |
| Method | GET |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

This yields the following response:
```json
{
  "status": "success",
  "data": [
    {
      "id": 1,
      "name": "Drawing Room",
      "home_id": 1
    },
    {
      "id": 2,
      "name": "Bedroom",
      "home_id": 1
    }
  ]
}
```

## Show room data by room ID

To show the data of a specific room by its ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:home_id/rooms/:id |
| Method | GET |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

For example, a GET request at http://ritanugoonj.in/homes/1/rooms/1 with the given headers could yield the following response (the data is a sammple, and it has no real existence):

```json
{
  "status": "success",
  "data": {
    "id": 1,
    "name": "Drawing Room",
    "home_id": 1,
    "user_id": 1
  }
}
```

If the room does not exist or if you don't have access to the room you are querying, then you get the following error with status code **404 Not Found**:
```json
{
  "status": "error",
  "data": {
    "message": "Room not found!"
  }
}
```

## Creating a room

To create a room, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:home_id/rooms |
| Method | POST |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

and use the following body (sample values given):

```json
{
  "name": "Drawing Room"
}
```

This yields the following response:
```json
{
  "status": "success",
  "data": {
    "id": 1,
    "name": "Drawing Room",
    "home_id": 1,
    "user_id": 1
  }
}
```

## Changing an existing room's data

To change the data of an existing home by it's ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:home_id/rooms/:id |
| Method | PUT |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

and use the following body (sample values given). Note that not all the keys are mandatory. It is recommended to put in only those keys that are to be changed:

```json
{
  "name": "Bedroom"
}
```

This yields a **204 No Content** blank response, which indicates that the values have been changed. In case of an error, you would get a detailed error message in the specified error response format (refer to [About the API](01_about_the_api.md)).

## Deleting a room

To delete an existing room by it's ID, use the following endpoint:

| Attribute | Value |
|---|---|
| URL | ritanugoonj.in/homes/:home_id/rooms/:id |
| Method | DELETE |
| Headers | Content-Type: *application/json* |
| | Authorization: *JWT your_token* |

> Note: *your_token* is the authorization token that you have to obtain by logging in. Refer to [Authentication](02_authentication.md) for more details.

This yields a **204 No Content** blank response, which indicates that the room has been deleted. In case of an error, you would get a detailed error message in the specified error response format (refer to [About the API](01_about_the_api.md)).
