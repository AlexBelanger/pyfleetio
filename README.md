# Fleetio Python API Wrapper

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Features](#features)
    - [Usage](#usage)
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
- [Feedback](#feedback)
- [Contributors](#contributors)
- [Acknowledgments](#acknowledgments)

## Introduction
**_pyfleetio_** allows you to send HTTP requests extremely easily to the Fleetio APi. This library is mostly based on the Requests library.
Learn more about Fleetio's API [here](https://developer.fleetio.com/). <br>


## Installation
```
pip install pyfleetio
```
## Features
- An API key needs to be generated using the following procedure [here](https://developer.fleetio.com/).
- Find your account specific [Token](https://developer.fleetio.com/).
- Provide those parameters to Fleetio class.

### Usage

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

## Feedback
If you have any questions, please reach out or by submitting an issue [here](https://github.com/AlexBelanger/pyfleetio/issues).
Feature requests are always welcome. If you wish to contribute, please take a quick look at the [guidelines](./CONTRIBUTING.md)!

## Acknowledgments
This library was developed with the fundamentals adapted from this API Wrapper [pyonfleet](https://github.com/onfleet/pyonfleet)

### **Note** This project is not affiliated, associated, authorized, endorsed by, or in any way officially connected with Fleetio Inc.
