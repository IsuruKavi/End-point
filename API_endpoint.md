# Login API

## POST `/login`

Use this endpoint to authenticate a user and obtain an access token.

### Request

- **URL**: `/login`
- **Method**: `POST`
- **Content-Type**: `application/json`

#### Request Body

```json
{
  "username": "exampleUser",
  "password": "examplePassword"
}
```

#### Response Body

HTTP/1.1 200 OK
Content-Type: application/json

```json
{
  "message": "Login successful",
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

HTTP/1.1 401 Unauthorized
consten-Type:application/json

```json
{
  "message": "Invalid username or passoword"
}
```

HTTP/1.1 400 Bad Request
consten-Type:application/json

```json
{
  "message": "Missing username or password"
}
```

HTTP/1.1 500 Server error
consten-Type:application/json

```json
{
  "message": "Internal Server Error"
}
```

# Register API

## POST `/register`

Use this endpoint to authenticate a user and obtain an access token.

### Request

- **URL**: `/register`
- **Method**: `POST`
- **Content-Type**: `application/json`

#### Request Body

```json
{
  "username": "newUser",
  "username": "exampleUser",
  "email": "newuser@example.com",
  "Second_language": "Sinhala"
}
```

#### Response Body

HTTP/1.1 201 Created
Content-Type: application/json

```json
{
  "message": "register successful"
}
```

HTTP/1.1 400 Bad Request
constent-Type:application/json

```json
{
  "message": "Missing required fields: username and/or password"
}
```

HTTP/1.1 409 Conflict
constent-Type:application/json

```json
{
  "message": "Username already exists. Please choose a different one."
}
```

HTTP/1.1 500 Internal Server Error
constent-Type:application/json

```json
{
  "message": "Internal Server Error."
}
```

# Translate API

## Overview

Use this API endpoint to translate a word into a specified language.

## Endpoint

- **URL**: `/translate`
- **Method**: `POST`
- **Content-Type**: `application/json`

## Headers

- **Authorization**: Bearer `token`

## Request Body

```json
{
  "word": "exampleWord",
  "language": "targetLanguageCode"
}
```

## Resoponse Body

HTTP/1.1 200 OK
constent-Type:application/json

```json
{
    {
  "word": "exampleWord",
  "english": "english_meanings",  // Provide English meanings if applicable
  "secondaryLanguage": {
    "info": [
      { "meaning": "translated_meaning" },
      { "definition": "translated_definition" }
    ],
    "language_iso_code": "targetLanguageCode",
    "language": "targetLanguageName"
  }
}

}
```

HTTP/1.1 401 Unauthorized
consten-Type:application/json

```json
{
  "error": "Unauthorized",
  "message": "Invalid or missing token"
}
```

HTTP/1.1 400 Bad Request
consten-Type:application/json

```json
{
  "error": "Bad Request",
  "message": "Missing word or language in request body"
}
```

HTTP/1.1 500 Internal Server Error
consten-Type:application/json

```json
{
  "error": "Internal Server Error",
  "message": "Something went wrong on the server"
}
```

# Search History API Documentation

## Overview

This API allows authenticated users to retrieve their search history.

## Authentication

Requests to this API endpoint (`/search-history`) must include a valid JWT (JSON Web Token) in the `Authorization` header using the `Bearer` scheme.



## GET `/search-history`

Use this endpoint to retrieve the search history for the authenticated user.

### Request

- **URL**: `/search-history`
- **Method**: `GET`
- **Headers**:
  - `Authorization: Bearer <your_access_token>`
  - `Content-Type: application/json`

### Response

#### Success Response

HTTP/1.1 200 OK
Content-Type: application/json

```json
{
  "history": [
    {"word1":{meaing}},{"word2":{meaing}},{"word3":{meaning}}
  ]
}
```
#### Error Responses

HTTP/1.1 401 Unauthorized
Content-Type: application/json

```json
{
  "message": "Unauthorized: Access token is missing or invalid"
}
```
HTTP/1.1 500 Unauthorized
Content-Type: application/json

```json
{
  "message": "Internal Server Error"
}
```