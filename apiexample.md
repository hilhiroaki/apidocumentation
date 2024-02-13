## Overview

This document describes a generic REST API, including introduction, HTTP Methods, HTTP response codes, Authentication, Request and Response.

### Table of Contents

* [Introduction](#introduction)
* [HTTP Methods](#http-methods)
* [HTTP Status Codes](#http-status-codes)
* [Authentication](#authentication)
* [Requests](#requests)
* [Responses](#responses)
* [Request and Response Examples](#request-and-response-examples)

### Introduction

REST is an acronym for REpresentational State Transfer and an architectural style for distributed hypermedia systems and it was first presented in 2000, by Roy Fielding. Since then, it became one of the most used approaches for building web-based Application Programming Interfaces (APIs).
All data is considered as a resource and has to be decoupled from their representation so the user can access the content in other formats, such as HTML, PDF, JSON, etc. The users and servers exchange representations of resources by using a standardized interface and protocol, which is usually HTTP, although is not mandatory by REST. Since is the most common, this documentation will describe the HTTP Methods.

### HTTP Methods

The HTTP method of an endpoind defines the action that is being performed on a resource. The most common HTTP methods are:
* GET: Used for retrieveing resources.
* POST: Used for creating resources.
* PATCH: Used for updating properties of resources.
* PUT: Used for replacing resources or collections of resources.
* DELETE: Used for deleting resources.

#### HTTP Status Codes

HTTP status codes provide information about the request made. The responses are divided in 5 classes:
* [100 - 199] Informational responses;
* [200 - 299] Successful responses;
* [300 - 399] Redirection messages;
* [400 - 499] Client error responses;
* [500 - 599] Server error responses.

Even though they are separated by these classes, each value has a specific meaning. For example Client error responses, which are between [400 - 499], each number indicates a different error response, as seen in the following table:

|CODE|MEANING|DESCRIPTION|
|---|---|---|
|400|Bad Request|The request was unaccepted, probably due to a missing parameter.|
|401|Unauthorized|No valid API key provided.|
|402|Request Failed|The request failed, even with valid parameters.|
|403|Forbidden|API key does not have permission to request.|
|404|Not Found|The requested resource does not exist.|

> In case you receive a response that is not in the range described, do not worry, they are a non-standard response. They are a custom response from the server you are making requests.

### Authentication

Some responses will only be retrieved if the user is authenticated, that is, has permission to access the information. Although some responses are accessible without authentication, being authenticated can return additional information. The two main ways to authenticate a user are with a username and password or with a secret token.

### Requests

A request is made of:
1. Endpoint: Url the user is requesting.
2. Method: Action that is being performed on a resource.
3. Headers: Provides information to the client and the server.
4. Data: The resource, or body. Information that is going to be sent to the server.
When you perform a request, you are requesting a specific information to the server. If you have access to the information, the server will return you a response with the information you requested.

### Responses

If the resource requested is found on the server, it must return a successful response (200, for instance) along with the response body. The response body usually comes in JSON format, with the requested information.

### Request and Response Examples

#### POST

~~~javascript
REQUEST
POST https://dummy.restapiexample.com/api/v1/create
{
    "name":"Hiro",
    "salary":"20k",
    "age":"27"
    }
~~~
~~~javascript
RESPONSE
{
    "status": "success",
    "data": {
        "name": "Hiro",
        "salary": "20k",
        "age": "27",
        "id": 8800
    },
    "message": "Successfully! Record has been added."
}
~~~


#### GET
~~~javascript
REQUEST
GET https://dummy.restapiexample.com/api/v1/employee/8800
~~~
~~~javascript
RESPONSE
{
  "status": "success",
  "data": {
          "id": "8800",
          "employee_name": "Hiro",
          "employee_salary": "20k",
          "employee_age": "27",
          "profile_image": ""
          }
}
~~~

