# Fleetio Python API Wrapper

## Table of Contents
- [Introduction](#introduction)
- [Installation](#installation)
- [Features](#features)
    - [Usage](#usage)
        * [GET Requests](#get-requests)
            - [Examples of `get()`]
            - [Examples of `get(id, queryParams)`]
        * [POST Requests](#post-requests)
            - [Examples of `create(body)`]
        * [PATCH Requests](#put-requests)
            - [Examples of `update(id, body)`]
        * [DELETE Requests](#delete-requests)
            - [Examples of `deleteOne(id)`]
    - [Throttling](#throttling)
    - [Responses](#responses)
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
#### GET Requests
##### Example 1
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

f = Fleetio(api_key, account_token)
active_contacts = f.contacts.get()
all_contacts = f.contacts.get(queryParams={"include_archived":"1"})
```
##### Example 2
```
import os
from fleetio import Fleetio, NotFoundError

api_key = '123456'
account_token = 'ABC123'

f = Fleetio(api_key, account_token)
active_vehicles = f.vehicles.get()
all_vehicles =  f.vehicles.get(queryParams={"include_archived":"1"})

my_car_id = '911'
try:
    my_car = f.vehicles.get(id=my_car_id)
except NotFoundError:
    print('Car not in active cars!')
```
#### POST Requests
##### Example 1
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

f = Fleetio(api_key, account_token)
best_car  = {
    'fuel_volume_units':'us_gallons',
    'meter_unit':'mi',
    'name':'Porsche 911',
    'ownership':'owned',
    'system_of_measurement':'imperial',
    'vehicle_type_id':'804609',
    'vehicle_status_id':'276263',
}

car_json = f.vehicles.create(body = best_car) # more fields are available https://developer.fleetio.com/docs/create-vehicle
```
##### Example 2
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

car_id = '123456'
f.vehicles.archive(id=car_id)
#
f.vehicles.restore(id=car_id)
```

#### PATCH Requests
##### Example
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

car_id = '123456'
f.vehicles.update(id=car_id, body = {'color':'Yellow', 'model':'Porsche'})
```

#### DELETE Requests
##### Example
```
import os
from fleetio import Fleetio

api_key = os.environ.get('FLEETIO_API_KEY')
account_token = os.environ.get('FLEETIO_ACCOUNT_TOKEN')

car_id = '123456'
f.vehicles.deleteOne(id=car_id)
```

### Throttling
Rate limiting is enforced by the API with a threshold of 20 requests per minute. Learn more about it [here](https://developer.fleetio.com/docs/response-codes). If more than 20 requests are sent within a minute, the requests go to sleep and wait as this ensures that every function invocation is successful at the cost of halting the thread.

### Responses
| Action | Endpoint | HTTP Verb | Description | Response Data Type |
| :---: | :---: | :---: | :---: | :---: |
|get()|/vehicles|GET|Returns an array of all vehicles.|Array|
|create|/vehicles|POST|Creates a new vehicle.|No content|
|get(id)|/vehicles/:id|GET|Returns the vehicle corresponding to the id parameter.|Hash|
|update(id)|/vehicles/:id|PATCH|Updates the vehicle corresponding to the id parameter.|No content|
|deleteOne(id)|/vehicles/:id|DELETE|Deletes the vehicle corresponding to the id parameter.|No content|


## Feedback
If you have any questions, please reach out or by submitting an issue [here](https://github.com/AlexBelanger/pyfleetio/issues).
Feature requests are always welcome. If you wish to contribute, please take a quick look at the [guidelines](./CONTRIBUTING.md)!

## Acknowledgments
This library was developed with the fundamentals adapted from this API Wrapper [pyonfleet](https://github.com/onfleet/pyonfleet)

#### **Disclaimer:** This project is not affiliated, associated, authorized, endorsed by, or in any way officially connected with Fleetio.com
