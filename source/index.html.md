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

# Authentication

Katara uses API keys to allow access to the API. You can register a new Katara's API key at our [developer portal](http://example.com/developers).

Katara expects for the API key to be included in all API requests to the server in a header that looks like the following:

`Authorization: Token token=YOUR_API_KEY`

<aside class="notice">
You must replace <code>YOUR_API_KEY</code> with your personal API key.
</aside>

<aside class="notice">
You have to know your <code>project_id</code>.
</aside>

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
    }],
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
      }
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
      }
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
        "photoURL": "http://www.images.com/image.png"
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
        "photoURL": "http://www.images.com/image.png"
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
      "photoURL": "http://www.images.com/image.png"
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



# Muscles Group

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


# Muscle

## Muscle Object

This is the JSON content of the returned muscles group object

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



