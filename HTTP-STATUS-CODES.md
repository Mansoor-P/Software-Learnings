# HTTP Status Codes Explained

HTTP status codes are issued by a server in response to a client's request. They provide information about the result of the request and help in identifying the outcome. This document offers a detailed overview of common HTTP status codes and their meanings.

## Table of Contents
- [Informational Responses (1xx)](#informational-responses-1xx)
  - [100 Continue](#100-continue)
  - [101 Switching Protocols](#101-switching-protocols)
- [Successful Responses (2xx)](#successful-responses-2xx)
  - [200 OK](#200-ok)
  - [201 Created](#201-created)
  - [204 No Content](#204-no-content)
- [Redirection Messages (3xx)](#redirection-messages-3xx)
  - [301 Moved Permanently](#301-moved-permanently)
  - [302 Found](#302-found)
  - [304 Not Modified](#304-not-modified)
- [Client Error Responses (4xx)](#client-error-responses-4xx)
  - [400 Bad Request](#400-bad-request)
  - [401 Unauthorized](#401-unauthorized)
  - [403 Forbidden](#403-forbidden)
  - [404 Not Found](#404-not-found)
  - [405 Method Not Allowed](#405-method-not-allowed)
- [Server Error Responses (5xx)](#server-error-responses-5xx)
  - [500 Internal Server Error](#500-internal-server-error)
  - [501 Not Implemented](#501-not-implemented)
  - [502 Bad Gateway](#502-bad-gateway)
  - [503 Service Unavailable](#503-service-unavailable)
  - [504 Gateway Timeout](#504-gateway-timeout)

## Informational Responses (1xx)
Informational responses are provisional responses. The client should be prepared to receive one or more 1xx responses before receiving a final response.

### 100 Continue
- **Description**: The server has received the request headers, and the client should proceed to send the request body.
- **Example**: A client sends a request with a large payload and includes an `Expect: 100-continue` header. The server responds with 100 Continue to indicate that it is ready to receive the request body.

### 101 Switching Protocols
- **Description**: The server acknowledges a request to switch protocols as indicated by the client.
- **Example**: A client requests to upgrade to WebSocket from HTTP by sending an `Upgrade` header. The server responds with 101 Switching Protocols to confirm the protocol change.

## Successful Responses (2xx)
These status codes indicate that the client’s request was successfully received, understood, and accepted.

### 200 OK
- **Description**: The request was successful, and the server has returned the requested data.
- **Example**: A client requests data from an API endpoint. The server returns the requested data with a 200 OK status.

### 201 Created
- **Description**: The request has been fulfilled, resulting in the creation of a new resource.
- **Example**: A client submits a form to create a new user. The server processes the request and creates the user, responding with 201 Created and including the location of the new user resource in the `Location` header.

### 204 No Content
- **Description**: The server successfully processed the request, but there is no content to return.
- **Example**: A client makes a successful DELETE request to remove a resource. The server confirms the deletion with a 204 No Content status.

## Redirection Messages (3xx)
These status codes indicate that further action needs to be taken by the client to complete the request.

### 301 Moved Permanently
- **Description**: The requested resource has been permanently moved to a new URL.
- **Example**: A client requests a URL that has been permanently moved to a new location. The server responds with 301 Moved Permanently and provides the new URL in the `Location` header.

### 302 Found
- **Description**: The requested resource has been temporarily moved to a different URL.
- **Example**: A client is redirected to a temporary URL for a resource. The server responds with 302 Found and provides the temporary URL in the `Location` header.

### 304 Not Modified
- **Description**: The resource has not been modified since the last request. The client can use the cached version.
- **Example**: A client requests a resource with an `If-Modified-Since` header. If the resource has not changed, the server responds with 304 Not Modified, indicating the client can use its cached version.

## Client Error Responses (4xx)
These status codes indicate that there was an error with the request made by the client.

### 400 Bad Request
- **Description**: The server could not understand the request due to invalid syntax.
- **Example**: A client submits a malformed request with incorrect syntax. The server responds with 400 Bad Request, indicating that the request could not be processed.

### 401 Unauthorized
- **Description**: The client must authenticate itself to get the requested response.
- **Example**: A client tries to access a protected resource without proper authentication. The server responds with 401 Unauthorized and may provide a `WWW-Authenticate` header indicating the required authentication scheme.

### 403 Forbidden
- **Description**: The client does not have access rights to the content.
- **Example**: A client is authenticated but does not have permission to access the requested resource. The server responds with 403 Forbidden.

### 404 Not Found
- **Description**: The server cannot find the requested resource.
- **Example**: A client requests a URL that does not exist. The server responds with 404 Not Found.

### 405 Method Not Allowed
- **Description**: The request method is known by the server but has been disabled and cannot be used.
- **Example**: A client sends a POST request to an endpoint that only supports GET requests. The server responds with 405 Method Not Allowed.

## Server Error Responses (5xx)
These status codes indicate that the server failed to fulfill a valid request.

### 500 Internal Server Error
- **Description**: The server encountered an unexpected condition that prevented it from fulfilling the request.
- **Example**: The server encounters an unexpected error while processing a request. It responds with 500 Internal Server Error, indicating a problem on the server side.

### 501 Not Implemented
- **Description**: The server does not support the functionality required to fulfill the request.
- **Example**: The client requests a method or feature that is not supported by the server. The server responds with 501 Not Implemented.

### 502 Bad Gateway
- **Description**: The server, while acting as a gateway or proxy, received an invalid response from the upstream server.
- **Example**: A server acting as a gateway receives a faulty response from an upstream server. It responds with 502 Bad Gateway.

### 503 Service Unavailable
- **Description**: The server is not ready to handle the request, often due to maintenance or overloading.
- **Example**: The server is temporarily down for maintenance. It responds with 503 Service Unavailable to indicate the service is not currently available.

### 504 Gateway Timeout
- **Description**: The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server.
- **Example**: A server acting as a proxy times out while waiting for a response from an upstream server. It responds with 504 Gateway Timeout.
