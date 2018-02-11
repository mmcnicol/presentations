
https://docs.atlas.mongodb.com/api/

Response Codes

Responses use the standard HTTP response codes, including:
Code 	Meaning 	Notes
200 	OK 	The request was successful. This is typically the response to a successful GET request.
201 	Created 	A new resource was created. This is typically the response to a successful POST request.
202 	Accepted 	A request for an asynchronous operation was accepted.
400 	Bad Request 	Something was wrong with the client request.
401 	Unauthorized 	Authentication is required but was not present in the request. Typically this means that the digest authentication information was omitted from the request, the provided credentials are incorrect, or the user associated with the given API key is not allowed to access the requested resource.
403 	Forbidden 	Access to the specified resource is not permitted.
404 	Not Found 	The requested resource does not exist.
405 	Method Not Allowed 	The HTTP method is not supported for the specified resource. Keep in mind that each resource may only support a subset of HTTP methods. For example, you are not allowed to DELETE the root resource.
409 	Conflict 	This is typically the response to a request to create or modify a property of an entity that is unique when an existing entity already exists with the same value for that property.
5xx 	Various server errors 	Something unexpected went wrong. Try again later and consider notifying Atlas Support.
Errors

When a request results in an error, the response body contains a document with additional details about what went wrong. The document contains three fields:

    error - The error code, which is simply the HTTP status code.
    reason - A short description of the error, which is simply the HTTP status phrase.
    detail - A more detailed description of the error.


