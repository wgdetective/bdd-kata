# Project for demonstration of BDD development kata

## Kata description

In the scope of this kata we'll go through implementation of 2 user stories and will solve 1 bug.

We'll work on microservice that should recommend content based on user answers to survey.

## Microservices

### survey-microservice

`GET /v1/surveys/${id}`
`200 OK`

```json
{
  "id": "S1",
  "name": "Initial Survey",
  "questions": [
    {
      "id": "Q1",
      "text": "Q1 TEXT",
      "multiplechoice": "false",
      "answers": [
        {
          "id": "A1",
          "text": "A1 TEXT",
          "tags": [
            "health"
          ]
        },
        {
          "id": "A2",
          "text": "A2 TEXT",
          "tags": [
            "health",
            "sport"
          ]
        },
        {
          "id": "A3",
          "text": "A3 TEXT",
          "tags": [
            "sport"
          ]
        }
      ]
    },
    {
      "id": "Q2",
      "text": "Q2 TEXT",
      "multiplechoice": "true",
      "answers": [
        {
          "id": "A2",
          "text": "A2 TEXT",
          "tags": [
            "health"
          ]
        },
        {
          "id": "A2",
          "text": "A2 TEXT",
          "tags": [
            "sport"
          ]
        },
        {
          "id": "A3",
          "text": "A3 TEXT",
          "tags": [
          ]
        }
      ]
    }
  ]
}
```

`GET /v1/user-answers`

```json
{
  "id": "ANS1",
  "userId": "userId",
  "answers": [
    {
      "surveyId": "S1",
      "questionId": "Q1",
      "answersIds": [
        "A2"
      ]
    },
    {
      "surveyId": "S1",
      "questionId": "Q2",
      "answersIds": [
        "A2",
        "A3"
      ]
    }
  ]
}
```

### content-product-microservice

`GET /v1/products?tag=?`

```json
[
  {
    "id": "P1",
    "name": "Product 1",
    "description": "Product 1 description",
    "tag": "sport",
    "creationDate": "2021-07-25T12:44:10.1414619"
  },
  {
    "id": "P2",
    "name": "Product 2",
    "description": "Product 2 description",
    "tag": "health",
    "creationDate": "2021-07-25T12:44:10.1414619"
  },
  {
    "id": "P3",
    "name": "Product 3",
    "description": "Product 3 description",
    "tag": "entertainment",
    "creationDate": "2021-07-25T12:44:10.1414619"
  }
]
```

### content-service-microservice

`GET /v1/services?tag=?`

```json
[
  {
    "id": "S1",
    "name": "Service 1",
    "description": "Service 1 description",
    "durability" : "24h",
    "tag": "sport",
    "creationDate": "2021-07-25T12:44:10.1414619"
  },
  {
    "id": "S2",
    "name": "Service 2",
    "description": "Service 2 description",
    "durability" : "24h",
    "tag": "health",
    "creationDate": "2021-07-25T12:44:10.1414619"
  },
  {
    "id": "S3",
    "name": "Service 3",
    "description": "Service 3 description",
    "durability" : "24h",
    "tag": "entertainment",
    "creationDate": "2021-07-25T12:44:10.1414619"
  }
]
```

### recommendation-microservice

TODO

## User stories

### 1. As a User I want to get list of recommended for me products and services.

API should return 3 items max.

### 2. Uncovered bug. Stability.
