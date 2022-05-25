System Management API
----------------------

This is a websocket application. Your socket connection correspondes to your session.

# User

## Register
**Request**

```json
    {
        "operation": "user/register",
        "body": {
            "name": "Max_Mustermann",
            "email": "ottonormal@gmx.de",
            "password": "high end secure"
        }
    }
```

**Response**

```json
    {
        "sucess": true
    }
```


## Login

**Request**

```json
    {
        "operation": "user/login",
        "body": {
            "name": "Max_Mustermann",
            "password": "high end secure"
        }
    }
```

**Response**

```json
    {
        "sucess": true
    }
```
## Session

will return the user identifier.

**Request**

```json
    {
        "operation": "user/session",
    }
```

**Response**

```json
    {
        "id": "UUID" 
    }
```

## Modifing Users

**Request**

```
    {
        "operation": "user/modify",
        "body": {
            "id": "UUID",
            "name": "New Maxmustermann",
            "email": "new_mail@protonmail.com",
            "password": "new_password",
            "role": 2
        }
    }
```

In order to make role updates you have to be administrator.

**Response**

```json
    {
        "sucess": true
    }
```

## Deleting Users

**Request**

```
    {
        "operation": "user/delete",
        "body": {
            "id": "UUID"
        }
    }
```

**Response**

```json
    {
        "sucess": true
    }
```

## Listing Users

Can only called by admin

**Request**

```
    {
        "operation": "user/list",
    }
```

**Response**

```json
    {
        "users": [
            {
                "id": "UUID",
                "name": "New Maxmustermann",
                "email": "new_mail@protonmail.com",
                "password": "new_password",
                "role": 2
            }
        ]
    }
```


# Regions


## Create Regions

**Request**

```json
    {
        "operation": "regions/create",
        body: {
            "name": "dresden",
            "frequency": 173000000,
            "transport_company": "dresdner verkehrs betriebe",
            "protocoll": ""
        }
    }
```

**Response**

```json
    {
        "success": true
    }
```


## List Regions

Returns all `regions`

**Request**

```json
    {
        "operation": "regions/list"
    }
```

**Response**

```json
    {
        "regions": [
            {
                "id": 0,
                "name": "dresden",
                "frequency": 173000000,
                "transport_company": "dresdner verkehrs betriebe",
                "protocoll": ""
            }
        ];
    }
```

# Stations

## Create Station

**Request**

```json
    {
        "operation": "station/create",
        "body": {
            "name": "Dresden Station Pieschen",
            "lat": 0.0,
            "lon": 0.0,
            "region": 0 # references to region 
        }
    }
```

**Response**

```json
    {
        "success": true
    }
```

## List Stations

**Request**

```json
    {
        "operation": "stations/list",
        "body": {
            "owner": "UUID", # optional
            "region": 0 # optional
        }
    }
```
if `owner` and `region` is set those will be used as filter.

**Response**

```json
    {
        "stations": [
            {
                "id": 0,
                "name": "Dresden Pieschen",
                "lat": 51.08106, 
                "lon": 13.72806,
                "region": 0, # reference to region with id 0
                "owner": "UUID" # reference to user with this id
            }
        ];
    }
```

