# Documentation for Sauti API

BaseURL: https://african-marketplace-bw.herokuapp.com

<details>
<summary><b>POST - Register a new user</b></summary>
<br>
<b>Endpoint:</b>  <code>BaseURL/api/auth/register</code>
<br>
<br>
Requires an object with an email and password, both string data types: 

```
{
	"email": "admin@email.com",
	"password": "password"
}
```

When successful will return status code of 201 (CREATED), the new user object and a token (example):

```
{
    "new_user": {
        "id": 2,
        "email": "admin@email.com",
        "name": null,
        "about": null,
        "avatar_url": null
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6kpXVCJ9..."
}
```
</details>

<details>
<summary><b>POST - Login a user</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/auth/login</code>
<br>
<br>
Requires an object with an email and password, both string data types: 

```
{
	"email": "admin@email.com",
	"password": "password"
}
```

When successful will return status code of 200 (OK), the new item object and a token (example):

```
{
    "user": {
        "id": 2,
        "email": "admin@email.com",
        "name": null,
        "about": null,
        "avatar_url": null
    },
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6kpXVCJ9..."
}
```
</details>

<details>
<summary><b>GET - Get a user by user id</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/users/:id</code>
<br>
<br>
Restricted endpoint. Token required.
<br>
<br>
No body required in the request. 
<br>
<br>
When successful will return status code of 200 (OK) and a single user object with an array of the items they've posted as well as their list of favorite items. Here is an example:

```
{
    "user": {
        "id": 1,
        "email": "admin@email.com",
        "name": null,
        "about": null,
        "avatar_url": null,
        "items": [
            {
                "id": 1,
                "name": "rice",
                "description": null,
                "photo_url": null,
                "city": "Ngozi",
                "country": "BDI",
                "price": 2,
                "created_at": "2019-10-21T04:58:11.423Z",
                "user_id": 1,
                "categories": [
                    {
                        "id": 2,
                        "type": "food",
                        "item_id": 1
                    }
                ]
            }
        ],
        "favorites": [
            {
                "item_id": 1,
                "user_id": 1,
                "id": 1,
                "name": "rice",
                "description": null,
                "photo_url": null,
                "city": "Ngozi",
                "country": "BDI",
                "price": 2,
                "created_at": "2019-10-21T04:58:11.423Z"
            }
        ]
    }
}
```
</details>

<details>
<summary><b>GET - Get a list of all items</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items</code>
<br>
<br>
Public access endpoint. No token required.
<br>
<br>
No body required in the request. 
<br>
<br>
When successful will return status code of 200 (OK) and an array of item objects. Here is an example:

```
[
    {
        "id": 1,
        "name": "rice",
        "description": null,
        "photo_url": null,
        "city": "Ngozi",
        "country": "BDI",
        "price": 2.25,
        "created_at": "2019-10-21T04:58:11.423Z",
        "user_id": 1
    },  
    {
        "id": 2,
        "name": "beans",
        "description": null,
        "photo_url": null,
        "city": "Ngozi",
        "country": "BDI",
        "price": 2.75,
        "created_at": "2019-10-21T04:58:11.423Z",
        "user_id": 2
    }
]
```
</details>

<details>
<summary><b>GET - Get any item by the item's id</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items/:id</code>
<br>
<br>
Public access endpoint. No token required.
<br>
<br>
No body required in the request. 
<br>
<br>
When successful will return status code of 200 (OK) and a single item object. Here is an example:

```
{
    "item": {
        "id": 1,
        "name": "rice",
        "description": null,
        "photo_url": null,
        "city": "Ngozi",
        "country": "BDI",
        "price": 2,
        "created_at": "2019-10-21T04:58:11.423Z",
        "user_id": 1,
        "categories": [
            {
                "id": 2,
                "type": "food",
                "item_id": 1
            }
        ]
    }
}
```
</details>

<details>
<summary><b>GET - Search for an item by name</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items/search/:value</code>
<br>
<br>
Public access endpoint. No token required.
<br>
<br>
No body required in the request. The value you send as the endpoint param will search for any item with a like name. It will ignore casing.
<br>
<br>
When successful will return status code of 200 (OK) and an arry of search results. Here is an example when we search for "ic":

```
[
    {
        "id": 2,
        "name": "Exotic Chicken",
        "description": "Fresh local honey that has no artificial ingredients.",
        "photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
        "city": "Ngozi",
        "country": "BDI",
        "price": 10.75,
        "created_at": "2019-10-21 22:43:36",
        "user_id": 1,
        "email": "admin@email.com",
        "username": "Amanda Lane",
        "about": null,
        "avatar_url": null
    },
    {
        "id": 3,
        "name": "Rice",
        "description": "Fresh local rice that has no artificial ingredients.",
        "photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
       "city": "Ngozi",
        "country": "BDI",
        "price": 2,
        "created_at": "2019-10-21 22:46:48",
        "user_id": 1,
        "email": "admin@email.com",
        "username": "Amanda Lane",
        "about": null,
        "avatar_url": null
    }
]
```
</details>

<details>
<summary><b>POST - Post a new item</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items</code>
<br>
<br>
Restricted endpoint. Token required.
<br>
<br>
Requires an object with the following required fields: "name", "city", "country", "price", and "user_id". All other fields are optional: 

```
{
	"name": "Unprocessed Honey",
	"description": "Fresh local honey that has no artificial ingredients.",
	"photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
	"city": "Ngozi",
    "country": "BDI",
	"price": 5.75,
	"user_id": 2
}
```

When successful will return status code of 201 (CREATED) and a single object of the newly created item. Here is an example:

```
{
    "id": 2,
    "name": "Unprocessed Honey",
    "description": "Fresh local honey that has no artificial ingredients.",
    "photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
   "city": "Ngozi",
        "country": "BDI",
    "price": 5.75,
    "created_at": "2019-10-21T17:44:05.057Z",
    "user_id": 2
}
```
</details>

<details>
<summary><b>PUT - Edit an item by item's id</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items/:id</code>
<br>
<br>
Restricted endpoint. Token required.
<br>
<br>
Requires an object with the field(s) being updated:

```
{
	"price": 10.75
}
```

When successful will return status code of 201 (CREATED) and a single object of the newly created item. Here is an example:

```
{
    "id": 2,
    "name": "Unprocessed Honey",
    "description": "Fresh local honey that has no artificial ingredients.",
    "photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
    "city": "Ngozi",
    "country": "BDI",
    "price": 10.75,
    "created_at": "2019-10-21T17:44:05.057Z",
    "user_id": 2
}
```
</details>

<details>
<summary><b>DELETE - Delete an item by item's id</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/items/:id</code>
<br>
<br>
Restricted endpoint. Token required.
<br>
<br>
No body required in the request. 
<br>
<br>
When successful will return an HTTP status code of 200 (OK) and a success message. Here is an example:

```
{
    "message": "Item successfully deleted from database."
}
```
</details>

<details>
<summary><b>POST - Add an item to a user's favorites list</b></summary>
<br>
<b>Endpoint:</b> <code>BaseURL/api/favorites/:user_id</code>
<br>
<br>
Restricted endpoint. Token required.
<br>
<br>
Requires a request body that is an object with the following shape. This is an example:

```
{
    "item_id": 4
}
```

When successful will return an HTTP status code of 200 (OK) and an array of that user's favorites like this: 

```
{
    "favorites": [
        {
            "item_id": 5,
            "user_id": 3,
            "id": 5,
            "name": "Unprocessed Honey",
            "description": "Fresh local honey that has no artificial ingredients.",
            "photo_url": "https://www.indianapolisorchard.com/wp-content/uploads/2014/02/apple-varieties-587.jpg",
            "city": "Ngozi",
            "country": "BDI",
            "price": 10.75,
            "created_at": "2019-10-21T20:02:38.641Z"
        }
    ]
}
```
</details>

### Table Entities

User Data 

| attribute  | data type | required                |
|------------|-----------|-------------------------|
| id         | integer   | auto-assigns            |
| email      | string    | Yes, and must be unique |
| password   | string    | Yes                     |
| username   | string    | No                      |
| about      | string    | No                      |
| avatar_url | string    | No                      |

Item Data

| attribute   | data type | required     |
|-------------|-----------|--------------|
| id          | integer   | auto-assigns |
| name        | string    | Yes          |
| description | string    | No           |
| photo_url   | string    | No           |
| city        | string    | Yes          |
| country     | string    | Yes          |
| price       | float     | Yes          |
| created_at  | timestamp | auto-assigns |
| user_id     | integer   | Yes          |

