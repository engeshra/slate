---
title: API Reference

<!-- language_tabs:
  - http -->

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/tripit/slate'>Documentation Powered by Slate</a>

search: true
---

# Introduction

Welcome to the venueSolutions API! You can use our API to access Katara Project endpoints.


This example API documentation page was created with [Slate](https://github.com/tripit/slate). Feel free to edit it and use it as a base for your own API's documentation.

## Authentication

Katara uses API keys to allow access to the API. You can register a new Katara's API key at our [developer portal](http://example.com/developers).

Katara expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=YOUR_API_KEY`

<aside class="notice">
You must replace <code>YOUR_API_KEY</code> with your personal API key.
</aside>

<aside class="notice">
You have to know your <code>project_id</code>.
</aside>

## Errors

> The JSON response for a succeed request:

```json
{
  "status": "success",
  "status_code": 200,
  "message": "Training program has been created successfully",
  "data": {
    "training_program": {
      "id": "3423422",
      "name": {"en": "Program_1", "ar": "برنامج"},
      "description": {"en": "Program_1_description", "ar": "برنامج"},
      "intencity": "medium",
      "exercises": [{
        "id": "3df3234s3"
        "name": "exercise#1",
        "description": "Machine#1 Desctiption"
      }]
    }
  }
}
```
> The JSON response for a failed request (data is null in all conditions):

```json
{
  "status": "fail",
  "status_code": 401,
  "message": "Invalid access token",
  "data": null
}
```
When an API request has been called, A response message will be returned. The response message will be in JSON format with 3 important keys. `status` will be set to one of the 2 values `success` OR `fail`, 
`message` will contain the message body of the response status, and `data` will contain the returned object after create or update.

<aside class="notice">
All responses are in JSON format
</aside>

`For succeed requests`

`HTTP Status: 200`

response body: {
  "status": "success",
  "status_code": 200,
  "message": "",
  "data": {

  }
}

HTTP Status | status (String) | status_code | message (String) | data
--------- | --------  | ------- | ----------- | --------
200 | success | 200 | XXX has been created successfully | XXX : {}



`For failed requests`

HTTP Status | status (String) | status_code | message (String) | data
--------- | --------  | ------  | ----------- | --------
401 | fail | 401 | Unauthorized - Invalid API key | null
403 | fail | 403 | forbidden – You do not have access to that record | null
404 | fail | 404 | Not Found | null
422 | fail | 422 | Unprocessable Entity | null
500 | fail | 500 | Server Error – We had a problem with our server. Try again later | null



# Training Programs

## Training Program Object

This is the JSON content of the returned training program object

### Training program attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | TrainingProgram ID
name | Hash | JSON Hash object of name locales 
description | Hash | JSON Hash object of name locales
Intensity | intensity | intensity object with those values [name: localizatedText (Hash), enumIndex: integer]
exercises | Array[Exercise] | array of all exercise included in this program


## GET: List Training Programs

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
[
  {
    "id": "3423422",
    "name": {"en": "Program_1", "ar": "برنامج"},
    "description": {"en": "Program_1_description", "ar": "برنامج"},
    "intencity": "medium",
    "exercises": [{
      "id": "3df3234s3"
      "name": "exercise#1",
      "description": "Machine#1 Desctiption"
    }]
  },
  {
      .........
  }
]
```

List all of all venue training prograns.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal


This endpoint retrieves all taining programs.


## GET: Retrieve Training Program

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
{
    "id": "3423422",
    "name": "Program_1",
    "description": "Program_1_description",
    "duration": "25 mins",
    "intencity": "medium",
    "musclesGroup": [{
      "id": "3423422",
      "name": "muscle_name",
      "image": {
        "url": "image-url"
      }
    }],
    "machines": [{
        "name": "Machine#1",
        "description": "Machine#1 Desctiption",
        "Locaiton": {
        },
        "muscles": [{
          "id": "3423422",
          "name": "muscle_name",
          "image": {
            "url": "image-url"
        }],
        "images": [{
          ""
        }]
      },
      ""
    }],
    
```

Retrieve training program by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | id of a certain training to be retrived


## DELETE: DELETE Training Programs

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "program 29622362 has been deleted."
}
```

Delete training program by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | id of a certain training to be retrived


## PUT: Update Training Programs


```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "program 29622362 has been deleted."
}
```

Update or PUT training program by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | id of a certain training to be retrived


<aside class="notice">
Any parameter from training program object
</aside>


## GET: All taining programs

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/all_taining_program'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
[
  {
    "id": "3423422",
    "name": {"en": "Program_1", "ar": "برنامج"},
    "description": {"en": "Program_1_description", "ar": "برنامج"},
    "intencity": "medium",
    "exercises": [{
      "id": "3df3234s3"
      "name": {"en": "exercise#1", "ar": "برنامج"},
      "description": {"en": "exercise#1 desctiption", "ar": "برنامج"},
      "photoURL": "http://www.images.com/image.png",
      "machine": {
        "id": "3423422",
        "name": {"en": "machine_1", "ar": ""},
        "description": "name": {"en": "description_1", "ar": ""},
        "providerLocationId": "2fg453222222",
        "photoURL": "http://www.images.com/image.png"
      }
      "primeMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "secondaryMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "stabilizerMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "coreMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "behavior": {
        "type": "reps_with_weight",
        "repetitions": {
          "count": 20,
          "weight": 20           
        },
        "duration": 0
      }
    }]
  },
  {
      .........
  }
]
```

List all of all venue training programs.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/all_taining_program`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal


<aside class="notice">
This request mainly used from the mobile side to encapsulate all data in one object
</aside>



# Exercise

## Exercise Object

This is the JSON content of the returned exercise object

### Exercise attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | Training machine ID
name | Hash | JSON Hash object of name locales { en: ..., ar: ..., ....}
description | Hash | JSON Hash object of name locales
machine | Machine | the machine used in this exercise
primeMoverMuscle | muscle | muscle objects 
secondaryMoverMuscle | muscle | muscle objects 
stabilizerMuscle | muscle | muscle objects 
coreMuscle | muscle | muscle objects 
photoURL | String | url of the exercise image
behavior | Hash | embedded object of those keys: [type, reps]. Type key will be one of the 3 values [reps_with_weight, duration, reps_without_weight] and Reps key, its value is an array of this object {"reps": Integer_value, "weight": Integer_value}
burnedCalories | Integer | the amount of calories that this exercise will burn


## GET: List of exercise for a certain Training Program

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
[{
      "id": "3df3234s3"
      "name": {"en": "exercise#1", "ar": "برنامج"},
      "description": {"en": "exercise#1 desctiption", "ar": "برنامج"},
      "photoURL": "http://www.images.com/image.png",
      "machine": {
        "id": "3423422",
        "name": {"en": "machine_1", "ar": ""},
        "description": "name": {"en": "description_1", "ar": ""},
        "providerLocationId": "2fg453222222",
        "photoURL": "http://www.images.com/image.png"
      }
      "primeMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "secondaryMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "stabilizerMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "coreMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "behavior": {
        "type": "reps_with_weight",
        "repetitions": {
          "count": 20,
          "weight": 20           
        },
        "duration": 0
      },
      "burnedCalories": 250
    }]
```

List all of all training program exercises.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | training program id, the owner of the exercises


This endpoint retrieves all exercises in this training program.


## GET: Retrieve a certain exercise

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises/:exercise_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
    {
      "id": "3df3234s3"
      "name": {"en": "exercise#1", "ar": "برنامج"},
      "description": {"en": "exercise#1 desctiption", "ar": "برنامج"},
      "photoURL": "http://www.images.com/image.png",
      "machine": {
        "id": "3423422",
        "name": {"en": "machine_1", "ar": ""},
        "description": "name": {"en": "description_1", "ar": ""},
        "providerLocationId": "2fg453222222",
        "photoURL": "http://www.images.com/image.png"
      }
      "primeMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "secondaryMoverMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "stabilizerMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "coreMuscle": {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      "behavior": {
        "type": "reps_with_weight",
        "repetitions": {
          "count": 20,
          "weight": 20           
        },
        "duration": 0
      },
      "burnedCalories": 250
    }
    
```

Retrieve training program by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises/:exercise_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | Training program id, the owner of the exercises
exercise_id | String | id of the requested exercise


## DELETE: DELETE Exercise

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "exercise 29622362 has been deleted."
}
```

Delete training program by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises/:exercise_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | Training program id, the owner of the exercises
exercise_id | String | id of the requested exercise


## PUT: Update Exercise


```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises/:exercise_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

PARAMS

{ 
  "exercise": { 
    "id": "23232323", 
    "name": { }, 
    ...., 
    "photoURL": "http://www.images.com/image2.png"
  }
}
```

> The above Request returns JSON structured like this:

```json
{
  ...
  "description": {"en": "exercise#1 desctiption", "ar": "برنامج"},
  "photoURL": "http://www.images.com/image2.png",
  ...
}
```

Update or PUT exercise by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/trainings/:training_id/exercises/:exercise_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
training_id | String | Training program id, the owner of the exercises
exercise_id | String | id of the requested exercise

### Query parameters

`params = { "exercise": { "id": "23232323", "name": { }, ...., "photoURL": "http://..."}}`

<aside class="notice">
Embedded the new object in the params with key <code>exercise</code>.
</aside>




# Machines

## Machine Object

This is the JSON content of the returned training machine object

### machine attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | Training machine ID
name | Hash | JSON Hash object of name locales
description | Hash | JSON Hash object of description locales
Location | Location | Location object is a hash { floor: FLOOR_ID, X: X_COORDINATE, y: y_COORDINATE }
providerLocationID | String | a returned value of the machine location that will be returned from the map provider
photoURL | String | url of the training machine
exercises | Array | list of exercise objects


## GET: List of machines

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/machines'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
      [{
        "id": "3423422",
        "name": {"en": "machine_1", "ar": ""},
        "description": "name": {"en": "description_1", "ar": ""},
        "providerLocationId": "2fg453222222",
        "photoURL": "http://www.images.com/image.png", 
        "exercises": [{
          "id": "3df3234s3"
          "name": {"en": "exercise#1", "ar": "برنامج"},
          "description": {"en": "exercise#1 desctiption", "ar": "برنامج"},
          "photoURL": "http://www.images.com/image.png",
          "machine": {
            "id": "3423422",
            "name": {"en": "machine_1", "ar": ""},
            "description": "name": {"en": "description_1", "ar": ""},
            "providerLocationId": "2fg453222222",
            "photoURL": "http://www.images.com/image.png"
          }
          "primeMoverMuscle": {
            "id": "34dfge2342",
            "name": {"en": "primeMoverMuscle_1", "ar": ""},
            "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
            "photoURL": "http://www.images.com/image.png",
            "muscleGroup": {
              "id": "4fsds34333",
              "name": {"en": "muscleGroup_1", "ar": ""}
            }
          },
          "secondaryMoverMuscle": {
            "id": "34dfge2342",
            "name": {"en": "primeMoverMuscle_1", "ar": ""},
            "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
            "photoURL": "http://www.images.com/image.png",
            "muscleGroup": {
              "id": "4fsds34333",
              "name": {"en": "muscleGroup_1", "ar": ""}
            }
          },
          "stabilizerMuscle": {
            "id": "34dfge2342",
            "name": {"en": "primeMoverMuscle_1", "ar": ""},
            "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
            "photoURL": "http://www.images.com/image.png",
            "muscleGroup": {
              "id": "4fsds34333",
              "name": {"en": "muscleGroup_1", "ar": ""}
            }
          },
          "coreMuscle": {
            "id": "34dfge2342",
            "name": {"en": "primeMoverMuscle_1", "ar": ""},
            "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
            "photoURL": "http://www.images.com/image.png",
            "muscleGroup": {
              "id": "4fsds34333",
              "name": {"en": "muscleGroup_1", "ar": ""}
            }
          },
          "behavior": {
            "type": "reps_with_weight",
            "repetitions": {
              "count": 20,
              "weight": 20           
            },
            "duration": 0
          }, 
          "burnedCalories": 200
        }]
      },
      ....
      ]
```

List all of all machines in this project.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/machines`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal


This endpoint retrieves all machines in this project.


## GET: Retrieve a certain muscle

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
      {
        "id": "3423422",
        "name": {"en": "machine_1", "ar": ""},
        "description": "name": {"en": "description_1", "ar": ""},
        "providerLocationId": "2fg453222222",
        "photoURL": "http://www.images.com/image.png",
        "exercises": [...]
      }
    
```

Retrieve machine by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
machine_id | String | id of the selected machine


## DELETE: DELETE Machine

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "machine :machine_id has been deleted."
}
```

Delete machine by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id'


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
machine_id | String | id of the selected machine


## PUT: Update Machine

```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

PARAMS
    {
      "id": "3423422",
      "name": {"en": "machine_1", "ar": ""},
      "description": "name": {"en": "description_1", "ar": ""},
      "providerLocationId": "2fg453222222",
      "photoURL": "http://www.images.com/image.png",
      "exercises" [.....]
    }
```

> The above Request returns JSON structured like this:

```json
{
  ...
  "description": {"en": "primeMoverMuscle__description", "ar": "برنامج"},
  "photoURL": "http://www.images.com/image2.png",
  ...
}
```

Update or PUT machine by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/machines/:machine_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
machine_id | String | id of the selected machine

### Query parameters

`params = { "machine": { "id": "23232323", "name": { }, ...., "photoURL": "http://..."}}`

<aside class="notice">
Embedded the new object in the params with key <code>machine</code>.
</aside>



# Muscles Groups

## MusclesGroup Object

This is the JSON content of the returned muscles group object

### muscles group attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | Training machine ID
name | Hash | localized names of muscle group (e.g. {"en": "leg", ... } )

## GET: List of muscle groups

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
[ 
  {
    "id": "4fsds34333",
    "name": {"en": "muscleGroup_1", "ar": ""}
  }
]
```

List all of all project muscle groups.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal


This endpoint retrieves all muscle groups created.


## GET: Retrieve a certain muscle group

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
  {
    "id": "4fsds34333",
    "name": {"en": "muscleGroup_1", "ar": ""}
  }
    
```

Retrieve muscle group by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_group_id | String | id of the requested muscle group


## DELETE: DELETE Exercise

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "muscle group 29622362 has been deleted."
}
```

Delete training program by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_group_id | String | id of the requested muscle group


## PUT: Update Exercise


```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

PARAMS

{ 
  "muscle_group":   {
    "id": "4fsds34333",
    "name": {"en": "muscleGroup_1", "ar": ""}
  }
}
```

> The above Request returns JSON structured like this:

```json
  "muscle_group": {
    "id": "4fsds34333",
    "name": {"en": "muscleGroup_1", "ar": ""}
  }
```

Update or PUT exercise by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/muscleGroups/:muscle_group_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_group_id | String | id of the requested muscle group

### Query parameters

`params = { "muscle_group": { "id": "23232323", "name": { }}}`

<aside class="notice">
Embedded the new object in the params with key <code>muscle_group</code>.
</aside>


# Muscles

## Muscle Object

This is the JSON content of the returned muscle object

### muscle attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | Training machine ID
name | Hash | JSON Hash object of name locales { en: ..., ar: ..., ....}
description | Hash | JSON Hash object of name locales
photoURL | String | url of the muscle image
musclesGroup | MusclesGroup | MusclesGroup Object hash e.g. { "id": "value", "name": { "en": "value1", "ar": "value2"} }


## GET: List of muscles

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
      [{
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      },
      ....
      ]
```

List all of all muscles in this project.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal


This endpoint retrieves all muscles in this project.


## GET: Retrieve a certain muscle

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
    {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle_1_description", "ar": ""},
        "photoURL": "http://www.images.com/image.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      }
    
```

Retrieve muscle by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_id | String | id of the selected muscle


## DELETE: DELETE Muscle

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "muscle :muscle_id has been deleted."
}
```

Delete muscle by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id'


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_id | String | id of the selected muscle


## PUT: Update Muscle

```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

PARAMS
    {
        "id": "34dfge2342",
        "name": {"en": "primeMoverMuscle_1", "ar": ""},
        "description": {"en": "primeMoverMuscle__description", "ar": ""},
        "photoURL": "http://www.images.com/image2.png",
        "muscleGroup": {
          "id": "4fsds34333",
          "name": {"en": "muscleGroup_1", "ar": ""}
        }
      }
```

> The above Request returns JSON structured like this:

```json
{
  ...
  "description": {"en": "primeMoverMuscle__description", "ar": "برنامج"},
  "photoURL": "http://www.images.com/image2.png",
  ...
}
```

Update or PUT exercise by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/muscles/:muscle_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
muscle_id | String | id of the selected muscle

### Query parameters

`params = { "muscle": { "id": "23232323", "name": { }, ...., "photoURL": "http://..."}}`

<aside class="notice">
Embedded the new object in the params with key <code>muscle</code>.
</aside>



# User Activities

## User Activity Object

This is the JSON content of the returned user activity object

### muscle attributes

Attribute | Type | Description
--------- | --------   | -----------
id | String | Training machine ID
activity_id | String | the id of the activity
activity_type | String | the type of the activity ["training_program", "exercise"]
status | String | current activity status [started, finished, skipped]


## GET: List of activities

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities'

HEADER 'Authorization: Token token=YOUR_API_KEY'

params { "user_id": logged_in_user_id }
```

> The above Request returns JSON structured like this:

```json
      [{
        "id": "34dfge2342",
        "activity_id": "3425222343",
        "activity_type": "training_program",
        "status": "started"
      },
      {
        "id": "54dfge2342",
        "activity_id": "99754kjs3",
        "activity_type": "exercise",
        "status": "finished"
      },
      ....
      ]
```

List all of all user activities.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities`


### Query parameters

Parameter | Type | Description
--------- | --------   | -----------
user_id | String | the logged in user id


This endpoint retrieves all activities for logged in user.


## GET: Retrieve a certain activity

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'
```

> The above Request returns JSON structured like this:

```json
      {
        "id": "54dfge2342",
        "activity_id": "99754kjs3",
        "activity_type": "exercise",
        "status": "finished"
      }
    
```

Retrieve activity by its id.

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
activity_id | String | id of the selected activity


## DELETE: DELETE activity

```shell
TYPE 'DELETE'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

```

> The above Request returns JSON structured like this:

```json
{
  "message": "activity :activity_id has been deleted."
}
```

Delete activity by id.

### HTTP Request

`DELETE http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id'


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
activity_id | String | id of the selected activity


## PUT: Update activity

```shell
TYPE 'PUT'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id'

HEADER 'Authorization: Token token=YOUR_API_KEY'

PARAMS
  {
    "user_activity" : {
        "id": "54dfge2342",
        "activity_id": "99754kjs3",
        "activity_type": "exercise",
        "status": "finished"
      }
  }
```

> The above Request returns JSON structured like this:

```json
  { 
    "user_activity" : {
        "id": "54dfge2342",
        "activity_id": "99754kjs3",
        "activity_type": "exercise",
        "status": "finished"
      }
  }
```

Update activity by id.

### HTTP Request

`PUT http://api.venueSolutions.com/spa/v1/projects/:project_id/userActivities/:activity_id`


### URL parameters

Parameter | Type | Description
--------- | --------   | -----------
project_id | String | Katra project id, you will get this id from katara user portal
activity_id | String | id of the selected activity

### Query parameters

`params = { "user_activity": { "id": "23232323", "activity_id": "242sdfs33", .... }`

<aside class="notice">
Embedded the new object in the params with key <code>user_activity</code>.
</aside>



# User Statistics


## GET: number of user visits

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_visits'

HEADER 'Authorization: Token token=YOUR_API_KEY'

params { "user_id": logged_in_user_id,
         "start_date": START_DATE,
         "end_date": END_DATE }
```

> The above Request returns JSON structured like this:

```json
      {
        "number_of_visits": 20
      }
```

Get the number of user visits

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_visits`


### Query parameters

Parameter | Type | Description
--------- | --------   | -----------
user_id | String | the logged in user id
start_date | Timestamp | the start date for the required data
end_date | Timestamp | the end date for the required data


This endpoint retrieves the number of visits for logged in user.


## GET: statistics for exercises

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_exercises_statistics'

HEADER 'Authorization: Token token=YOUR_API_KEY'

params { "user_id": logged_in_user_id,
         "start_date": START_DATE,
         "end_date": END_DATE }
```

> The above Request returns JSON structured like this:

```json
      {
        "number_of_started_exercises": 20,
        "number_of_finished_exercises": 20,
        "number_of_skipped_exercises": 10
      }
```

Get exercises statistics of logged in user 

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_exercises_statistics`


### Query parameters

Parameter | Type | Description
--------- | --------   | -----------
user_id | String | the logged in user id
start_date | Timestamp | the start date for the required data
end_date | Timestamp | the end date for the required data


This endpoint retrieves the current, completed, skipped exercises for logged in user.


## GET: statistics for burned calories

```shell
TYPE 'GET'

URL 'http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_burned_calories'

HEADER 'Authorization: Token token=YOUR_API_KEY'

params { "user_id": logged_in_user_id,
         "start_date": START_DATE,
         "end_date": END_DATE }
```

> The above Request returns JSON structured like this:

```json
      {
        "total_burned_calories": 440,
        "burned_calories": {
          "2017-01-20": {
            "00": 12,
            ...
            "23": 23
          }
        }
      }
```

Get burned calories for logged in user

### HTTP Request

`GET http://api.venueSolutions.com/spa/v1/projects/:project_id/get_user_burned_calories`


### Query parameters

Parameter | Type | Description
--------- | --------   | -----------
user_id | String | the logged in user id
start_date | Timestamp | the start date for the required data
end_date | Timestamp | the end date for the required data


This endpoint retrieves total burned calories for logged in user.

