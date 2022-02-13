# 101_REST_API_First_Steps
REST APIs enable you to develop all kinds of web applications having all possible CRUD (create, retrieve, update, delete) operations.

## Table of Contents
* [HTTP GET](#http-get)
* [HTTP POST](#http-post)
* [HTTP PUT](#http-put)
* [HTTP DELETE](#http-delete)
* [HTTP PATCH](#http-patch)
* [Summary](#summary)

## Http GET
Use GET requests to retrieve resource representation/information only – and not modify it in any way. As GET requests do not change the resource’s state, these are said to be safe methods.

### GET API Response Codes
* 200 (OK) - If the resource is found.
* 404 (NOT FOUND) - If the resource is not found.
* 400 (BAD REQUEST) - If the request is not correctly formed.

### Example URL's
```sh 
HTTP GET http://www.appdomain.com/users
HTTP GET http://www.appdomain.com/users?size=20&page=5
HTTP GET http://www.appdomain.com/users/123
HTTP GET http://www.appdomain.com/users/123/address
```

## Http POST
Use POST APIs to create new subordinate resources, e.g., a file is subordinate to a directory containing it or a row is subordinate to a database table. When talking strictly about REST, POST methods are used to create a new resource into the collection of resources.

### GET API Response Codes
* 201 (CREATED) - If the resource is created.
* 200 (OK) or 204 (No Content) - If the created result can't be identified by uri.

### Example URL's
```sh 
HTTP POST http://www.appdomain.com/users
HTTP POST http://www.appdomain.com/users/123/accounts
```

## Http PUT
Use PUT APIs primarily to update an existing resource (if the resource does not exist, then API may decide to create a new resource or not).

### GET API Response Codes
* 201 (CREATED) - If the resource is created.
* 200 (OK) or 204 (No Content) - If an exiting resource is modified

### Example URL's
```sh 
HTTP PUT http://www.appdomain.com/users/123
HTTP PUT http://www.appdomain.com/users/123/accounts/456
```

## Http DELETE
As the name applies, DELETE APIs delete the resources (identified by the Request-URI).

### GET API Response Codes
* 200 (OK) - The resource has been deleted.
* 202 (ACCEPTED) - The action has been queued.
* 204 (No Content) - The action has been performed but the response does not include an entity.
* 404 (NOT FOUND) - The resource has been deleted before.

### Example URL's
```sh 
HTTP DELETE http://www.appdomain.com/users/123
HTTP DELETE http://www.appdomain.com/users/123/accounts/456
```

## Http PATCH
HTTP PATCH requests are to make a partial update on a resource.

## Summary
| HTTP Method | CRUD | Collection Resource (e.g. /users) | Single Resouce (e.g. /users/123)| 
| :--- | :--- | :--- | :--- |
| POST | Create | 201 (Created), ‘Location’ header with link to /users/{id} containing new ID | Avoid using POST on a single resource| 
| GET | Read | 200 (OK), list of users. Use pagination, sorting, and filtering to navigate big lists | 200 (OK), single user. 404 (Not Found), if ID not found or invalid |
| PUT | Update/Replace | 405 (Method not allowed), unless you want to update every resource in the entire collection of resource | 200 (OK) or 204 (No Content). Use 404 (Not Found), if ID is not found or invalid |
| PATCH | Partial Update/Modify | 405 (Method not allowed), unless you want to modify the collection itself | 200 (OK) or 204 (No Content). Use 404 (Not Found), if ID is not found or invalid |
| DELETE | Delete | 405 (Method not allowed), unless you want to delete the whole collection — use with caution | 200 (OK). 404 (Not Found), if ID not found or invalid |
