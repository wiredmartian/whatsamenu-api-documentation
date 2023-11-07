
# Table of Contents
<!-- TOC -->

- [WhatsAMenu API](#whatsamenu-api)
    - [Supported Enums](#supported-enums)
        - [Used Status Codes](#http-status-codes)
        - [Provinces](#provinces)
    - [Authentication](#authentication)
        - [Accepted Headers](#accepted-headers)
    - [API](#api)
        - [Auth & Accounts](#auth-and-accounts)
            - [Create New User Account](#new-user-account)
            - [User Login](#login-user)                   
            - [Generate API Key](#generate-api-key)       
            - [Generate API Key](#forgot-password)        
            - [Forgot Password](#reset-password)
        - [Restaurants](#restaurants)
            - [List Restaurants](#list-restaurants)                  
            - [Create Restaurant](#new-restaurant)                   
            - [Update Restaurant](#update-restaurant)
            - [Create Alias](#create-restaurant-id-alias)
            - [Get Restaurant By Id](#get-restaurant-by-id)         
            - [Get Restaurant By Alias](#get-restaurant-by-alias)
            - [List Restaurant Menus](#list-restaurant-menus)        
            - [Delete Restaurant](#delete-restaurant)                
            - [List Restaurants Near Me](#restaurants-near-me)       
            - [Search Restaurants](#search-restaurants)              
            - [List Restaurants By Owner](#list-restaurants-by-owner)
            - [Create Restaurant Menu](#create-restaurant-menu)      
            - [Get Restaurant QR Code](#get-restaurant-qr-code)      
            - [Upload Restaurant Banner](#upload-restaurant-banner)
        - [Menu](#menu)
            - [Get Menu](#get-menu)                  
            - [Ask About Menu](#ask-about-menu)      
            - [Delete Menu](#delete-menu)            
            - [Create Menu Group](#create-menu-group)
            - [List Menu Groups](#list-menu-groups)
        - [Menu Group](#menu-group)
            - [Update Menu Group](#update-menu-group)              
            - [Delete Menu Group](#delete-menu-group)              
            - [Create Grouped Menu Item](#create-grouped-menu-item)
            - [List Grouped Menu Items](#list-grouped-menu-items)
        - [Menu Item](#menu-item)
            - [Get Menu Item](#get-menu-item)                            
            - [Update Menu Item](#update-menu-item)                      
            - [Delete Menu Item](#delete-menu-item)                      
            - [Create Menu Item Allergen](#create-menu-item-allergen)    
            - [List Menu Item Allergens](#list-menu-item-allergens)      
            - [Delete Menu Item Allergen](#delete-menu-item-allergen)    
            - [Create Menu Item Ingredient](#create-menu-item-ingredient)
            - [List Menu Item Ingredients](#list-menu-item-ingredients)  
            - [Upload Menu Item Image](#upload-menu-item-image)
        - [Ingredients](#ingredient)
            - [Update Ingredient](#update-ingredient)            
            - [Delete Ingredient](#delete-ingredient)            
            - [Upload Ingredient Image](#upload-ingredient-image)
        - [Allergen](#allergen)
            - [List Allergens](#list-allergens)
            - [Get Allergen](#get-allergen)

<!-- /TOC -->
<!-- Generated with https://marketplace.visualstudio.com/items?itemName=AlanWalk.markdown-toc -->

# WhatsAMenu API

In the age of digital transformation, dining out has taken a new turn with technology at its forefront. Gone are the days of flipping through traditional paper menus or scanning QR codes only to be redirected to a plain PDF file. Now, with WhatsAMenu (What's a menu?), you can dive into the world of verbose menus, offering a detailed look at what's on your plate.

WhatsAMenu is a restaurant menu API that allows restaurants to describe their food items down to the finest details. Food category, ingredients, allergens, and associated images are all on display. You'll no longer have to guess what you're ordering. With this level of transparency, you can make informed choices about what you eat.


This API only returns data in a **JSON** format. It also accepts data in **JSON** format, unless otherwise specified.

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/7238091-c337fbed-43fc-4a66-870c-3cfbdc1167e2?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D7238091-c337fbed-43fc-4a66-870c-3cfbdc1167e2%26entityType%3Dcollection%26workspaceId%3Df7aedb7c-b2ff-43da-b219-270fbd08a6e3)

### Supported Enums

#### Provinces

| Province      | Description                         |
|---------------|-------------------------------------|
| EASTERN_CAPE  | Eastern Cape                        |
| WESTERN_CAPE  | Western Cape                        |
| NORTHERN_CAPE | Northern Cape                       |
| NORTH_WEST    | North West                          |
| GAUTENG       | Gauteng                             |
| MPUMALANGA    | Mpumalanga                          |
| LIMPOMPO      | Limpopo                             |
| FREE_STATE    | Free State                          |
| KWAZULU_NATAL | KwaZulu-Natal                       |


#### HTTP Status Codes

These are the only response status codes to be expected from this API

| Status                      |
|-----------------------------|
| [200] - Ok                  | 
| [201] - Created             | 
| [400] - BadRequest          | 
| [401] - Unauthorized        | 
| [403] - Forbidden           | 
| [500] - InternalServerError | 

## Authentication
- Bearer
- API Key

**WhatsAMenu API** currently supports **Bearer** token or the **API Key** for authentication. You receive a bearer token when you log into
the system. You need the bearer token to generate the initial API key. Any subsequent API Keys can be generated using
a bearer token or an API key.

### Accepted Headers

The Bearer token is passed through the `Authorization` header. And the API key can **only** be passed through the
`X-API-Key` header.

| Key           | Allowed                                                                        |
|---------------|--------------------------------------------------------------------------------|
| Authorization | Bearer Token                                                                   |
| X-API-Key     | API Key                                                                        |
| Content-Type  | - `application/json` <br/> - `multipart/form-data` <br/> - `text/event-stream` |


## API


These are all the version 1 `/v1/` endpoints available to manage restaurants, accounts and menu.


| Action                                                      | Method | Resource                                                         | Current Status |
|-------------------------------------------------------------|--------|------------------------------------------------------------------|----------------|
| **Auth & Account endpoints**                                |        |                                                                  |                |
| [Create New User Account](#new-user-account)                | POST   | `v1/auth/sign-up`                                                | `DONE`         |
| [User Login](#login-user)                                   | POST   | `v1/auth/sign-in`                                                | `DONE`         |
| [Generate API Key](#generate-api-key)                       | POST   | `v1/auth/api-key`                                                | `DONE`         |
| [Generate API Key](#forgot-password)                        | POST   | `v1/auth/forgot-password`                                        | `DONE`         |
| [Forgot Password](#reset-password)                          | POST   | `v1/auth/reset-password`                                         | `DONE`         |
| **Restaurant endpoints**                                    |        |                                                                  |                |
| [List Restaurants](#list-restaurants)                       | GET    | `v1/restaurants`                                                 | `IN PROGRESS`  |
| [Create Restaurant](#new-restaurant)                        | POST   | `v1/restaurants`                                                 | `DONE`         |
| [Update Restaurant](#update-restaurant)                     | PUT    | `v1/restaurants`                                                 | `DONE`         |
| [Create Alias](#create-restaurant-id-alias)                 | POST   | `v1/restaurants/{id}/alias`                                      | `DONE`         |
| [Get Restaurant By Id](#get-restaurant-by-id)               | GET    | `v1/restaurants/{id}`                                            | `DONE`         |
| [Get Restaurant By Alias](#get-restaurant-by-alias)         | GET    | `v1/restaurants/{alias}/alias`                                   | `DONE`         |
| [List Restaurant Menus](#list-restaurant-menus)             | GET    | `v1/restaurants/{id}/menus`                                      | `DONE`         |
| [Delete Restaurant](#delete-restaurant)                     | DELETE | `v1/restaurants/{id}`                                            | `DONE`         |
| [List Restaurants Near Me](#restaurants-near-me)            | POST   | `v1/restaurants/near-me`                                         | `DONE`         |
| [Search Restaurants](#search-restaurants)                   | GET    | `v1/restaurants/search?query={term}&limit={limit}`               | `DONE`         |
| [List Restaurants By Owner](#list-restaurants-by-owner)     | GET    | `v1/restaurants/owner`                                           | `DONE`         |
| [Create Restaurant Menu](#create-restaurant-menu)           | POST   | `v1/restaurants/{id}/menu`                                       | `DONE`         |
| [Get Restaurant QR Code](#get-restaurant-qr-code)           | GET    | `v1/restaurants/{id}/qrcode`                                     | `DONE`         |
| [Upload Restaurant Banner](#upload-restaurant-banner)       | PUT    | `v1/restaurants/{id}/upload`                                     | `DONE`         |
| **Menu endpoints**                                          |        |                                                                  |                |
| [Get Menu](#get-menu)                                       | GET    | `v1/menu/{id}`                                                   | `DONE`         |
| [Ask About Menu](#ask-about-menu)                           | GET    | `v1/menu/enquire?menuId={menuId}&userId={userId}&prompt={query}` | `IN PROGRESS`  |
| [Delete Menu](#delete-menu)                                 | DELETE | `v1/menu/{id} `                                                  | `DONE`         |
| [Create Menu Group](#create-menu-group)                     | POST   | `v1/menu/{id}/menu-group`                                        | `DONE`         |
| [List Menu Groups](#list-menu-groups)                       | GET    | `v1/menu/{id}/menu-group`                                        | `DONE`         |
| **Menu Group endpoints**                                    |        |                                                                  |                |
| [Update Menu Group](#update-menu-group)                     | PUT    | `v1/menu-group/{id}`                                             | `DONE`         |
| [Delete Menu Group](#delete-menu-group)                     | DELETE | `v1/menu-group/{id}`                                             | `DONE`         |
| [Create Grouped Menu Item](#create-grouped-menu-item)       | POST   | `v1/menu-group/{id}/menu-items`                                  | `DONE`         |
| [List Grouped Menu Items](#list-grouped-menu-items)         | GET    | `v1/menu-group/{id}/menu-items`                                  | `DONE`         |
| **Menu Item endpoints**                                     |        |                                                                  |                |
| [Get Menu Item](#get-menu-item)                             | GET    | `v1/menu-item/{id}`                                              | `DONE`         |
| [Update Menu Item](#update-menu-item)                       | PUT    | `v1/menu-item/{id}`                                              | `DONE`         |
| [Delete Menu Item](#delete-menu-item)                       | DELETE | `v1/menu-item/{id}`                                              | `DONE`         |
| [Create Menu Item Allergen](#create-menu-item-allergen)     | POST   | `v1/menu-item/{id}/allergens`                                    | `DONE`         |
| [List Menu Item Allergens](#list-menu-item-allergens)       | GET    | `v1/menu-item/{id}/allergens`                                    | `DONE`         |
| [Delete Menu Item Allergen](#delete-menu-item-allergen)     | DELETE | `v1/menu-item/{id}/allergens/{allergenId}`                       | `IN PROGRESS`  |
| [Create Menu Item Ingredient](#create-menu-item-ingredient) | POST   | `v1/menu-item/{id}/ingredients`                                  | `DONE`         |
| [List Menu Item Ingredients](#list-menu-item-ingredients)   | GET    | `v1/menu-item/{id}/ingredients`                                  | `DONE`         |
| [Upload Menu Item Image](#upload-menu-item-image)           | PUT    | `v1/menu-item/{id}/upload`                                       | `DONE`         |
| **Ingredient endpoints**                                    |        |                                                                  |                |
| [Update Ingredient](#update-ingredient)                     | PUT    | `v1/ingredients/{id}`                                            | `DONE`         |
| [Delete Ingredient](#delete-ingredient)                     | DELETE | `v1/ingredients/{id}`                                            | `DONE`         |
| [Upload Ingredient Image](#upload-ingredient-image)         | PUT    | `v1/ingredients/{id}/upload`                                     | `DONE`         |
| **Allergen endpoints**                                      |        |                                                                  |                |
| [List Allergens](#list-allergens)                           | GET    | `v1/allergens`                                                   | `DONE`         |
| [Get Allergen](#get-allergen)                               | GET    | `v1/allergens/{id}`                                              | `DONE`         |


## Auth And Accounts

### New User Account

Signing up for a new account

#### Auth

- Anonymous

#### Request

`POST v1/auth/sign-up`

#### Example body

Password Policy:
- At least 8 characters long
- At least 1 special character (-+_!@#$%^&*.,?)
- At least one numeric character
- At least one lowercase and uppercase character

```json
{
  "email": "sbu@example.com",
  "password": "#Sbu2@3$"
}
```

#### Example responses

`[201 - Created]`

```json
{
  "message": "user account created"
}
```

`[400 - Bad Request]`

```json
{
  "error": "Email already exists"
}
```

```json
{
  "error": "password must at least be 8 characters"
}
```


### Login User

Login user into the API

#### Auth

- Anonymous

#### Request

`POST v1/auth/sign-in`

#### Example body

```json
{
  "email": "sbu@example.com",
  "password": "#Sbu2@3$"
}
```

#### Example responses

`[200 - OK]`

```json
{
  "token": "ey.............."
}
```

`[401 - Unauthorized]`

```json
{
  "error": "incorrect email or password"
}
```


### Generate API Key

Generates a new API Key. **WARN**: a user and API key exist in a **one-to-one** relationship.
Generating a new key invalidates any previously existing key for a user.

#### Auth

- Bearer

#### Request

`POST v1/auth/api-key`

#### Example

There is **no request body required** to generate a new key

#### Responses

`[200 - OK]`

```json
{
  "apiKey": "WM.NFrS_pfq4_R2_bda6ZUrph9w8QqV1hrIUGe1NJ1olQ8RTO3qD2Jy_dcSqFB-3zqp"
}
```

`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "Cannot perform this action at this time"
}
```

### Forgot Password

Sends an OTP (One-Time PIN) to the email inbox that will be used to reset the password

#### Auth

- Anonymous

#### Request

`POST v1/auth/forgot-password`

#### Example

```json
{
  "email": "sbu@example.com"
}
```

#### Responses

`[200 - OK]`

```json
{
  "message": "A One Time Pin has been sent to your email"
}
```

### Reset Password

Resets the user's forgotten password

#### Auth

- Anonymous

#### Request

`POST v1/auth/reset-password`

#### Example

```json
{
  "email": "sbu@example.com",
  "password": "P@$$w0rd!!",
  "otp": "701950"
}
```

#### Responses

`[200 - OK]`

```json
{
  "message": "Password reset successful"
}
```

`[400 - OK]`

```json
{
  "message": "Incorrect One Time PIN (OTP)"
}
```

`[400 - OK]`

```json
{
  "message": "OTP has expired"
}
```

## Restaurants

Endpoints to manage, search and filter restaurants

### New Restaurant

Creates a new restaurant

#### Auth

- API Key

#### Request

`POST - v1/restaurants`

**JSON BODY**

Consists of restaurant information, and it's address including geo-coordinates (used to locate restaurant)

| Key       | Required | Description                      |
|:----------|:---------|:---------------------------------|
| line1     | true     | Address Line 1                   |
| line2     | false    | Optional Address Line 2          |
| city      | true     | City                             |
| state     | true     | Province (check supported enums) |
| country   | false    | Optional country                 |
| latitude  | true     | Latitude                         |
| longitude | true     | Longitude                        |
| name      | true     | Restaurant name                  |
| summary   | true     | Short restaurant headline        |


#### Example

```json
{
  "line1": "311 Peter Mokaba Rd",
  "line2": "Morningside",
  "city": "Durban",
  "state": "KWAZULU_NATAL",
  "country": "South Africa",
  "latitude": 12.34385833,
  "longitude": -13.238437,
  "name": "Kota Place Restaurant",
  "summary": "We sell the best kotas in Morningside"
}
```

#### Responses

`[201 - Created]`

```json
{
  "message": "restaurant created"
}
```

`[401 - Unauthorized]`

```json
{
  "error": "unable to get user claims"
}
```

`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "`Name` is a required field"
}
```



### Update Restaurant

Updates an existing restaurant details

#### Auth

- API key

#### Request

`PUT - v1/restaurants/{restaurantId}`

**JSON BODY**


| Key       | Required | Description                      |
|:----------|:---------|:---------------------------------|
| line1     | true     | Address Line 1                   |
| line2     | false    | Optional Address Line 2          |
| city      | true     | City                             |
| state     | true     | Province (check supported enums) |
| country   | false    | Optional country                 |
| latitude  | true     | Latitude                         |
| longitude | true     | Longitude                        |
| name      | true     | Restaurant name                  |
| summary   | true     | Short restaurant headline        |


#### Example

```json
{
  "line1": "311 Peter Mokaba Rd",
  "line2": "Morning side",
  "city": "Durban",
  "state": "KWAZULU_NATAL",
  "country": "South Africa",
  "latitude": 12.34385833,
  "longitude": -13.238437,
  "name": "Kota Place",
  "summary": "We sell the best kotas in Durban"
}
```

#### Responses

`[200 - Ok]`

```json
{
  "message": "restaurant updated"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

`[400 - Bad Request]`

```json
{
  "error": "`City` is a required field"
}
```

`[500 - InternalServerError]`

```json
{
  "error": "An error has occurred while updating restaurant"
}
```

### Create Restaurant Id Alias

Creates an alias for a restaurant. The alias is unique and formatted more like a username

#### Auth

- API key

#### Request

`POST - v1/restaurants/{id}/alias`

**JSON BODY**


| Key   | Required | Description                     |
|:------|:---------|:--------------------------------|
| alias | true     | Restaurant id alias, e.g dukkah |


#### Example

```json
{
  "alias": "Dukkah Durban"
}
```

#### Responses

`[200 - Ok]`

```json
{
  "data": "dukkah-durban"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

`[400 - Bad Request]`

```json
{
  "error": "entry already exists"
}
```

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```


### List Restaurants

`TODO`: refactor

Returns a list of unordered restaurants

#### Auth

- API key

#### Request

`GET v1/restaurants`

#### Example responses


`[200 - OK]`

```json
[
  {
    "restaurantId": "134",
    "name": "SALT Morningside",
    "summary": "We make the best burgers in Morningside",
    "distance": null,
    "imageUrl": "public/restaurants/134-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
    "address": {
      "addressId": "1",
      "line1": "Florida Morningside",
      "line2": "311 Peter Mokaba Road",
      "city": "Durban",
      "state": "KWAZULU_NATAL",
      "country": "South Africa",
      "latitude": 12.088,
      "longitude": 12.088
    },
    "updated": "",
    "created": ""
  }
]
```

`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```

### Get Restaurant By Id

Gets a restaurant by its id 

#### Auth

- API key

#### Request

`GET v1/restaurants/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "restaurantId": "134",
  "alias": "salt-morningside",
  "name": "SALT Morningside",
  "summary": "We make the best burgers in Morningside",
  "distance": null,
  "imageUrl": "public/restaurants/134-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
  "address": {
    "addressId": "1",
    "line1": "Florida Morningside",
    "line2": "311 Peter Mokaba Road",
    "city": "Durban",
    "state": "KWAZULU_NATAL",
    "country": "South Africa",
    "latitude": 12.088,
    "longitude": 12.088
  },
  "updated": "2022-01-02 12:19:30",
  "created": "2022-01-02 12:19:30"
}
```

`[404 - Not Found]`
```json
{
  "error": "Restaurant not found"
}
```
`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```

### Get Restaurant By Alias

Gets a restaurant by its alias, the alias is unique per restaurant, and it is a nullable field

#### Auth

- API key

#### Request

`GET v1/restaurants/{alias}`

#### Example responses

`[200 - OK]`

```json
{
  "restaurantId": "134",
  "alias": "salt-morningside",
  "name": "SALT Morningside",
  "summary": "We make the best burgers in Morningside",
  "distance": null,
  "imageUrl": "public/restaurants/134-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
  "address": {
    "addressId": "1",
    "line1": "Florida Morningside",
    "line2": "311 Peter Mokaba Road",
    "city": "Durban",
    "state": "KWAZULU_NATAL",
    "country": "South Africa",
    "latitude": 12.088,
    "longitude": 12.088
  },
  "updated": "2022-01-02 12:19:30",
  "created": "2022-01-02 12:19:30"
}
```

`[404 - Not Found]`
```json
{
  "error": "Restaurant not found"
}
```
`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```


### Restaurants Near Me

Lists restaurants found near specified geolocation coordinates. The `distance` is in meters. The `radius` is in kilometers

#### Auth

- API key

#### Request

`POST v1/restaurants/near-me`

#### Example

**JSON BODY**

```json
{
  "latitude": -29.791040,
  "longitude": 31.028410,
  "radius": 20
}
```

#### Responses

`[200 - OK]`

```json
[
  {
    "restaurantId": "14",
    "name": "The Ocean Terrace - The Oyster Box Hotel",
    "summary": null,
    "distance": 8.89917396396982,
    "imageUrl": "public/restaurants/14-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
    "address": {
      "addressId": "33",
      "line1": "Umhlanga",
      "line2": "Oyter Box Hotel",
      "city": "Durban",
      "state": "KwaZulu-Natal",
      "country": "",
      "latitude": -29.727597,
      "longitude": 31.087159
    },
    "updated": "2022-01-02 12:19:30",
    "created": "2022-01-02 12:19:30"
  }
]
```

`[400 - Bad Request]`

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```


### Delete Restaurant

Marks a restaurant for deletion. **NB** Deleting a restaurant will also remove any items associated with it,
such as a **menu**, **address**, **menu items**, **groups**, and **ingredients**.

#### Auth

- API Key

#### Request

`DELETE v1/restaurants/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "message": "item deleted"
}
```

`TODO`: Finish auth on this endpoint


### Search Restaurants

Search for restaurants by name

#### Auth

- API key

#### Request

`GET v1/restaurants/search?query={searchTerm}&limit={limit}`

- Query Params

| Param | Required | Description                                                    |
|:------|:---------|:---------------------------------------------------------------|
| query | true     | Search query, i.e restaurant name. **NB**: length must be >= 3 |
| limit | false    | Number of results to be returned, **default**: 10              |


#### Example responses

`[200 - OK]`

```json
[
  {
    "restaurantId": "1",
    "name": "SALT Morningside",
    "summary": "We make the best burgers in Morningside",
    "distance": null,
    "imageUrl": "public/restaurants/1-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
    "address": {
      "addressId": "1",
      "line1": "Florida Morningside",
      "line2": "311 Peter Mokaba Road",
      "city": "Durban",
      "state": "KwaZulu-Natal",
      "country": "",
      "latitude": 12.0881728,
      "longitude": 12.019378
    },
    "updated": "2022-06-23 22:49:15",
    "created": "2022-06-23 22:49:15"
  }
]
```

`[400 - Bad Request]`

```json
{
  "error": "missing required search input"
}
```

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```


### List Restaurants By Owner

Get a list of restaurant by owner (current authenticated user request)

#### Auth

- API key

#### Request

`GET v1/restaurants/owner`

#### Example responses

`[200 - OK]`

```json
[
  {
    "restaurantId": "61",
    "name": "Dukkah Florida",
    "summary": "Hey",
    "distance": null,
    "imageUrl": "",
    "address": {
      "addressId": "80",
      "line1": "Kensignton",
      "line2": "2nd Beach road",
      "city": "Durbz",
      "state": "KWAZULU_NATAL",
      "country": "",
      "latitude": 0.16364,
      "longitude": 1.92384872
    },
    "updated": "2023-08-11 19:18:05",
    "created": "2023-07-29 19:47:26"
  }
]
```

`[401 - Bad Request]`

```json
{
  "error": "cannot acquire user claims"
}
```

`[500 - InternalServerError]`

```json
{
  "error": "an unexpected error has occurred while processing request"
}
```


### Create Restaurant Menu

Creates a menu and associates it with a restaurant

#### Auth

- API Key

#### Request

`PUT - v1/restaurants/{id}/menu`

**JSON BODY**


| Key       | Required | Description           |
|:----------|:---------|:----------------------|
| name      | true     | Menu name             |
| summary   | false    | Brief summary of menu |


#### Example

```json
{
  "name": "Steers Menu",
  "summary": "Ultimate menu"
}
```

#### Responses

`[201 - Created]`

```json
{
  "message": "menu created"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

`[400 - Bad Request]`

```json
{
  "error": "`Name` is a required field"
}
```

### List Restaurant Menus

Returns a list of restaurant menu, and no additional menu data such as menu items, groups or ingredients

#### Auth

- API key

#### Request

`GET v1/restaurants/{id}/menus`

#### Example response

`[200 - Ok]`

```json
[
  {
    "menuId": "4",
    "name": "Butcher Boys Morningside",
    "summary": null,
    "restaurantId": "10",
    "menuGroups": null,
    "updated": "2023-04-09 15:38:59",
    "created": "2023-04-09 15:38:59"
  }
]
```


### Get Restaurant QR Code

Returns a base64 QR Code image which is just a link to the restaurant's menu

#### Auth

- API key

#### Request

`GET v1/restaurants/{id}/qrcode`

#### Example response

`[200 - Ok]`

```json
{
  "imageUri": "data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAA..."
}
```


### Upload Restaurant Banner

Uploads a restaurant display/banner image

### Image Criteria
- PNG / JPG / JPEG
- < 1MB

#### Auth

- API Key

#### Request

`PUT v1/restaurants/{id}/upload`

#### Body

Content-Type: `multipart/form-data`


| Key        | Required | Type                                  |
|------------|----------|---------------------------------------|
| fileData   | true     | file                                  |

#### Example response

`[200 - OK]`

```json
{
  "data": "public/restaurants/5-b2a7f1c6be9edf1ac591c123b6ed2f90.jpg"
}
```

`[400 - BadRequest]`

```json
{
  "error": "image too large"
}
```



## Menu

### Ask About Menu

Ask any questions related to the menu, such as allergens, food type, your budget etc. This uses an AI model
underneath with the context of the menu

- Query Params

| Param  | Required | Description                                        |
|:-------|:---------|:---------------------------------------------------|
| userId | true     | The user's identifier, used to retain user context |
| menuId | true     | The menu in question                               |
| prompt | true     | The query about the menu                           |

#### Request

`GET v1/menu/enquire`


#### Example Response

This returns a stream of JSON responses.
This is best used with an <a href="https://developer.mozilla.org/en-US/docs/Web/API/EventSource">EventSource</a>

| Data                         | Time         |
|:-----------------------------|:-------------|
| ```{"content":"For"}```      | 22:08:48.059 | 
| ```{"content":" a"}```       | 22:08:48.060 | 
| ```{"content":" seafood"}``` | 22:08:48.061 | 
| ```{"content":" option"}```  | 22:08:48.062 | 
| ```{"content":" within"}```  | 22:08:48.062 | 
| ```{"content":" a"}```       | 22:08:48.062 | 
| ```{"content":" R250"}```    | 22:08:48.063 | 
| ```{"content":" budget"}```  | 22:08:48.063 | 



### Create Menu Group

Creates a menu group/section/category within the main menu

#### Auth

- API Key

#### Request

`POST v1/menu/{id}/menu-group`

**JSON BODY**

| Key       | Required | Description                    |
|:----------|:---------|:-------------------------------|
| name      | true     | Menu group/category name       |
| summary   | false    | Brief summary of menu category |

#### Example body

```json
{
  "name": "Beverages",
  "summary": "All you can drink"
}
```

#### Example responses

`[200 - OK]`

```json
{
  "message": "menu group created"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Get Menu

Returns the menu of the restaurant with all associated items

**Menu Structure**
- Menu
    - Menu Groups[]
        - Menu Items[]
            - Ingredients[]

#### Auth

- API key

#### Request

`GET v1/menu/{id}`

#### Example response

`[200 - Ok]`
```json
{
  "menuId": "2",
  "name": "Dukkah Restaurant & Bar",
  "summary": "Dukkah Restaurant & Bar on Durban’s Florida road is a high point on the durban dining scene - a modern and luxuriant social hub with an upscale cocktail bar and lounge. ",
  "restaurantId": "8",
  "menuGroups": [
    {
      "menuId": "2",
      "menuGroupId": "9",
      "name": "Starters",
      "summary": "",
      "items": [
        {
          "menuItemId": "15",
          "menuId": "2",
          "menuGroupId": "9",
          "name": "Chicken Croquettes",
          "summary": "Thyme, anchovies, onion, garlic, mustard, chilli, Grana Padano, celery dressing",
          "description": "Thyme, anchovies, onion, garlic, mustard, chilli, Grana Padano, celery dressing",
          "imageUrl": "",
          "price": 110,
          "ingredients": [],
          "updated": "2023-04-03 20:37:23",
          "created": "2023-04-03 20:37:23"
        },
        {
          "menuItemId": "22",
          "menuId": "2",
          "menuGroupId": "9",
          "name": "Salt and Pepper Squid",
          "summary": "Deep fried, asian slaw, aioli",
          "description": "Deep fried, asian slaw, aioli",
          "imageUrl": "",
          "price": 95,
          "ingredients": [],
          "updated": "2023-04-03 20:54:54",
          "created": "2023-04-03 20:54:54"
        }
      ],
      "updated": "2023-04-02 15:58:53",
      "created": "2023-04-02 15:58:53"
    },
    {
      "menuId": "2",
      "menuGroupId": "11",
      "name": "Pasta",
      "summary": "",
      "items": [
        {
          "menuItemId": "27",
          "menuId": "2",
          "menuGroupId": "11",
          "name": "Chili Prawn Fettuccine",
          "summary": "Napoli, coriander, grated pecorino",
          "description": "Napoli, coriander, grated pecorino",
          "imageUrl": "",
          "price": 175,
          "ingredients": [],
          "updated": "2023-04-04 18:11:12",
          "created": "2023-04-04 18:11:12"
        },
        {
          "menuItemId": "30",
          "menuId": "2",
          "menuGroupId": "11",
          "name": "Seafood Linguini",
          "summary": "Chardonnay cream, prawns, mussels, squid, chili, gremolata",
          "description": "Chardonnay cream, prawns, mussels, squid, chili, gremolata",
          "imageUrl": "",
          "price": 195,
          "ingredients": [],
          "updated": "2023-04-04 18:13:39",
          "created": "2023-04-04 18:13:39"
        }
      ],
      "updated": "2023-04-02 15:59:27",
      "created": "2023-04-02 15:59:27"
    }
  ],
  "updated": "2023-04-02 15:37:51",
  "created": "2023-04-02 15:37:51"
}
```


### Delete Menu

Marks a menu for deletion. **NB** Deleting a menu will also remove any items associated with it,
such as **menu items**, **groups**, and **ingredients**.

#### Auth

- API Key

#### Request

`DELETE v1/menu/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "message": "item deleted"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

## Menu Group

### Update Menu Group

Updates a menu group

#### Auth

- API Key

#### Request

`PUT v1/menu-group/{id}`


**JSON BODY**

| Key       | Required | Description                    |
|:----------|:---------|:-------------------------------|
| name      | true     | Menu group/category name       |
| summary   | false    | Brief summary of menu category |

#### Example body

```json
{
  "name": "Meat",
  "summary": "All you can eat meat meals"
}
```

#### Example responses

`[200 - OK]`

```json
{
  "message": "menu group updated"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Delete Menu Group

Deletes a menu group and all menu items attached to it

#### Auth

- API Key

#### Request

`DELETE v1/menu-group/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "message": "item deleted"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### List Menu Groups

Lists all menu groups (categories) found under a menu

#### Auth

- API Key

#### Request

`GET v1/menu/{id}/menu-groups`

#### Example response

`[200 - Ok]`
```json
[
  {
    "menuId": "1",
    "menuGroupId": "11",
    "name": "Sides",
    "summary": "Sides",
    "items": null,
    "updated": "2022-01-08 12:21:43",
    "created": "2022-01-08 12:21:43"
  },
  {
    "menuId": "1",
    "menuGroupId": "12",
    "name": "Sharing",
    "summary": "Sharing",
    "items": null,
    "updated": "2022-01-08 12:21:43",
    "created": "2022-01-08 12:21:43"
  }
]
```

### List Grouped Menu Items

List all menu items under a menu group/category/section

#### Auth

- API Key

#### Request

`GET v1/menu-group/{id}/menu-items`

#### Example response

`[200 - OK]`

```json
[
  {
    "menuItemId": "46",
    "menuId": "18",
    "menuGroupId": "20",
    "name": "Ice Cream",
    "summary": "Dessert that will melt your taste away",
    "description": "Dessert that will melt your taste away",
    "imageUrl": "",
    "price": 13.65,
    "ingredients": null,
    "updated": "",
    "created": ""
  }
]
```

### Create Grouped Menu Item

Create a menu item under a group/category

#### Auth

- API Key

#### Request

`POST v1/menu-group/{id}/menu-items`


**JSON BODY**

| Key         | Required | Description                   |
|:------------|:---------|:------------------------------|
| name        | true     | Menu item name                |
| summary     | true     | Brief summary of menu item    |
| description | false    | Full details of the menu item |
| price       | false    | Price of the item             |
| allergens   | false    | Menu items allergens          |

#### Example body

```json
{
  "name": "Medium Chips",
  "summary": "Get any two awesome burgers for the price of one",
  "description": "The wacky wednesday special gives you 2 chicken or beef",
  "price": 20.39,
  "allergens": ["3", "5"]
}
```

#### Example responses

`[200 - OK]`

```json
{
  "message": "menu item created"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

## Menu Item

### Get Menu Item

Gets a menu item by id

#### Auth

- API Key

#### Request

`GET v1/menu-item/{id}`

#### Example response

`[200 - Ok]`

```json
{
  "menuItemId": "10",
  "menuId": "1",
  "menuGroupId": "9",
  "name": "Another Item",
  "summary": "For those extra good mornings, start your day with a seasoned boerie patty, egg, ketchup and onion on a freshly toasted bun.",
  "description": "For those extra good mornings, start your day with a seasoned boerie patty, egg, ketchup and onion on a freshly toasted bun.",
  "imageUrl": "public/menu-items/1-b74b2b6acf4a14235ba2219b7511a34c.jpeg",
  "price": 3,
  "ingredients": null,
  "updated": "2022-03-06 17:45:33",
  "created": "2022-03-06 17:45:33"
}
```

### Update Menu Item

Update a menu item

#### Auth

- API key

#### Request

`PUT v1/menu-item/{id}`

**JSON BODY**

| Key         | Required | Description                    |
|:------------|:---------|:-------------------------------|
| name        | true     | Menu item name                 |
| summary     | true     | Brief summary of menu item     |
| description | false    | Full details of the menu item  |
| price       | false    | Price of the item              |
| menuGroupId | true     | Menu group the item belongs to |

#### Example body

```json
{
  "name": "Nice Ice Cream",
  "summary": "Best ice cream in the Milky-Way",
  "description": "Melting ice-cream",
  "price": 20.39,
  "menuGroupId": 20
}
```

#### Example responses

`[200 - OK]`

```json
{
  "message": "menu item updated"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Delete Menu Item

Marks a menu item for deletion

#### Auth

- API Key

#### Request

`DELETE v1/menu-item/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "message": "item deleted"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Create Menu Item Ingredient

Creates/adds an allergen to a menu item

#### Auth

- API Key

#### Request

`POST v1/menu-item/{id}/ingredients`

**JSON BODY**

| Key         | Required | Description     |
|:------------|:---------|:----------------|
| name        | true     | Ingredient name |


#### Example body

```json
{
  "name": "Tomato"
}
```

#### Example response

`[201 - Created]`

```json
{
  "message": "ingredient created"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Create Menu Item Allergen

Creates/adds an allergen to a menu item

#### Auth

- API Key

#### Request

`POST v1/menu-item/{id}/allergens`

**JSON BODY**

| Key        | Required | Description                             |
|:-----------|:---------|:----------------------------------------|
| allergenId | true     | Allergen id, use /v1/allergens for list |

#### Example body

```json
{
  "allergenId": "7"
}
```

#### Example responses

`[201 - Created]`

```json
{
  "message": "allergen added"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

`[500 - InternalServerError]`

```json
{
  "error": "MenuItem or Allergen was not found"
}
```

### List Menu Item Ingredients

List all ingredients of a menu item

#### Auth

- API Key

#### Request

`GET v1/menu-item/{id}/ingredients`

#### Example response

`[200 - OK]`

```json
[
  {
    "ingredientId": "1",
    "menuItemId": "1",
    "name": "Regular Bun",
    "imageUrl": "public/ingredients/1-40a1afc36b3ee3a9d4164c3c0dc3ded5.png",
    "updated": "2022-01-08 12:37:50",
    "created": ""
  }
]
```

### List Menu Item Allergens

Lists all allergens for a menu item

#### Auth

- API Key

#### Request

`GET v1/menu-item/{id}/allergens`

#### Example response

```json
[
  {
    "allergenId": "2",
    "menuItemId": "16",
    "name": "Nuts",
    "summary": "Contains nuts",
    "updated": "",
    "created": ""
  }
]
```

### Upload Menu Item Image

Uploads a menu item display image

### Image Criteria
- PNG / JPG / JPEG
- < 1MB

#### Auth

- API Key

#### Request

`PUT v1/menu-item/{id}/upload`

#### Body

Content-Type: `multipart/form-data`


| Key        | Required | Type                                  |
|------------|----------|---------------------------------------|
| fileData   | true     | file                                  |

#### Example response

`[200 - OK]`

```json
{
  "data": "public/menu-items/5-b2a7f1c6be9edf1ac591c123b6ed2f90.jpg"
}
```

`[400 - BadRequest]`

```json
{
  "error": ".gif file type is not allowed"
}
```



## Ingredient

### Update Ingredient

Updates an ingredient of a menu item

#### Auth

- API Key

#### Request

`PUT v1/ingredients/{id}`

**JSON BODY**

| Key        | Required | Description                     |
|:-----------|:---------|:--------------------------------|
| name       | true     | Ingredient new name             |
| menuItemId | true     | Menu item the ingredient is for |

#### Example body

```json
{
  "name": "Cheese",
  "menuItemId": 542
}
```

#### Example responses

`[200 - OK]`

```json
{
  "message": "ingredient updated"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Delete Ingredient

Marks an ingredient for deletion

#### Auth

- API Key

#### Request

`DELETE v1/ingredients/{id}`

#### Example responses

`[200 - OK]`

```json
{
  "message": "ingredient deleted"
}
```

`[403 - Forbidden]`

```json
{
  "error": "explicit deny: user not permitted to modified resource"
}
```

### Upload Ingredient Image

Uploads an ingredient image

### Image Criteria
- PNG / JPG / JPEG
- < 1MB

#### Auth

- API Key

#### Request

`PUT v1/ingredients/{id}/upload`

#### Body

Content-Type: `multipart/form-data`


| Key        | Required | Type                                  |
|------------|----------|---------------------------------------|
| fileData   | true     | file                                  |

#### Example response

`[200 - OK]`

```json
{
  "data": "public/ingredients/5-b2a7f1c6be9edf1ac591c123b6ed2f90.jpg"
}
```

`[400 - BadRequest]`

```json
{
  "error": "image too large"
}
```



## Allergen

### Get Allergen

Looks up an allergen by its id

#### Auth

- API Key

#### Request

`GET v1/allergens/{id}`

#### Example response

`[200 - Ok]`
```json
{
  "allergenId": "2",
  "name": "Nuts",
  "summary": "Nuts",
  "updated": "",
  "created": ""
}
```


### List Allergens

Returns a list of all allergens

#### Auth

- API Key

#### Request

`GET v1/allergens`

#### Example response

`[200 - Ok]`
```json
[
  {
    "allergenId": "2",
    "name": "Nuts",
    "summary": "Nuts",
    "updated": "",
    "created": ""
  }
]
```
