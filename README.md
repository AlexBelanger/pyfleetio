# Fleetio Python API Wrapper
Learn more about Fleetio's API [here](https://developer.fleetio.com/). <br>
If you have any questions, please reach out or by submitting an issue [here](https://github.com/AlexBelanger/pyfleetio/issues).

## Table of contents
* [Table of contents](#table-of-contents)
* [Introduction](#introduction)
* [Installation](#installation)
* [Usage](#usage)
    - [Throttling](#throttling)
    - [Responses](#responses)
    - [Supported CRUD operations](#supported-crud-operations)
        * [GET Requests](#get-requests)
            - [Examples of `get()`]
            - [Examples of `get(param)`]
        * [POST Requests](#post-requests)
            - [Examples of `create()`]
        * [PATCH Requests](#put-requests)
            - [Examples of `update()`]
        * [DELETE Requests](#delete-requests)
            - [Examples of `deleteOne()`]

## Introduction
This library provides simple access to the Fleetio's API.

## Installation
```
pip install pyfleetio
```
## Usage
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

f = Fleetio(api_key, account_token)
active_contacts = f.contacts.get()
all_contacts = f.contacts.get(queryParams={"include_archived":"1"})
```

### Throttling
Rate limiting is enforced by the API with a threshold of 20 requests per minute. Learn more about it [here](https://developer.fleetio.com/docs/response-codes).

### Responses

## Special Mention
This library was developed with the fundamentals adapted from this API Wrapper [pyonfleet](https://github.com/onfleet/pyonfleet)

###This project is not affiliated with Fleetio.
