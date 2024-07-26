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

---

## Informational Responses (1xx)

Informational responses are provisional responses. The client should be prepared to receive one or more 1xx responses before receiving a final response.

### 100 Continue

- **Description**: Indicates that the server has received the request headers and the client should proceed to send the request body. This response is used in situations where the client needs to wait for the server's approval before sending a large request body.
- **Example**: A client sends a POST request with a large payload and includes an `Expect: 100-continue` header. The server responds with `100 Continue` to indicate that it is ready to receive the request body.

### 101 Switching Protocols

- **Description**: The server acknowledges a request to switch protocols as indicated by the client. This status code is sent in response to an `Upgrade` header in the request.
- **Example**: A client requests to upgrade to WebSocket from HTTP by sending an `Upgrade` header. The server responds with `101 Switching Protocols` to confirm the protocol change.

## Successful Responses (2xx)

These status codes indicate that the client's request was successfully received, understood, and accepted.

### 200 OK

- **Description**: The request was successful, and the server has returned the requested data. This is the most common status code for successful responses.
- **Example**: A client requests data from an API endpoint such as `/api/users/123`. The server retrieves the user data and responds with `200 OK`, including the user information in the response body.

### 201 Created

- **Description**: The request has been fulfilled, resulting in the creation of a new resource. The new resource's URL is typically provided in the `Location` header.
- **Example**: A client submits a POST request to create a new user with details in the request body. The server processes the request, creates the user, and responds with `201 Created`, including the URL of the new user in the `Location` header (e.g., `/api/users/124`).

### 204 No Content

- **Description**: The server successfully processed the request, but there is no content to return. This status code is often used for successful DELETE requests.
- **Example**: A client makes a DELETE request to remove a user resource at `/api/users/123`. The server successfully deletes the user but responds with `204 No Content` since there is no additional information to return.

## Redirection Messages (3xx)

These status codes indicate that further action needs to be taken by the client to complete the request.

### 301 Moved Permanently

- **Description**: The requested resource has been permanently moved to a new URL. The new URL is provided in the `Location` header.
- **Example**: A client requests a URL that has been permanently moved. The server responds with `301 Moved Permanently` and provides the new URL (e.g., `/new-url`) in the `Location` header.

### 302 Found

- **Description**: The requested resource has been temporarily moved to a different URL. The new URL is provided in the `Location` header. Unlike `301 Moved Permanently`, this status code indicates that the resource may return to the original URL in the future.
- **Example**: A client requests a URL that has been temporarily redirected. The server responds with `302 Found` and provides the temporary URL (e.g., `/temporary-url`) in the `Location` header.

### 304 Not Modified

- **Description**: The resource has not been modified since the last request. The client can use the cached version of the resource. This status code is typically used with cache validation headers.
- **Example**: A client requests a resource with an `If-Modified-Since` header indicating the last known modification date. If the resource has not changed, the server responds with `304 Not Modified`, allowing the client to use its cached version.

## Client Error Responses (4xx)

These status codes indicate that there was an error with the request made by the client.

### 400 Bad Request

- **Description**: The server could not understand the request due to invalid syntax. This status code indicates that the client should modify the request to correct the syntax issues.
- **Example**: A client submits a POST request with invalid JSON data. The server responds with `400 Bad Request`, indicating that the request could not be processed due to malformed syntax.

### 401 Unauthorized

- **Description**: The client must authenticate itself to get the requested response. This status code indicates that authentication is required and has either failed or has not been provided.
- **Example**: A client attempts to access a protected resource without providing authentication credentials. The server responds with `401 Unauthorized`, and the `WWW-Authenticate` header may indicate the required authentication scheme (e.g., `Bearer`).

### 403 Forbidden

- **Description**: The client does not have access rights to the content. This status code indicates that the server understood the request but refuses to authorize it.
- **Example**: A client is authenticated but does not have the necessary permissions to access a resource. The server responds with `403 Forbidden`, indicating that access is denied.

### 404 Not Found

- **Description**: The server cannot find the requested resource. This status code indicates that the URL requested by the client does not exist on the server.
- **Example**: A client requests a URL that does not exist (e.g., `/api/nonexistent`). The server responds with `404 Not Found`, indicating that the resource could not be found.

### 405 Method Not Allowed

- **Description**: The request method is known by the server but has been disabled for the requested resource. This status code indicates that the method used in the request is not allowed for the resource.
- **Example**: A client sends a POST request to an endpoint that only supports GET requests. The server responds with `405 Method Not Allowed`, and the `Allow` header may list the allowed methods (e.g., `GET`).

## Server Error Responses (5xx)

These status codes indicate that the server failed to fulfill a valid request.

### 500 Internal Server Error

- **Description**: The server encountered an unexpected condition that prevented it from fulfilling the request. This status code is a generic error message indicating that something went wrong on the server side.
- **Example**: The server encounters an unexpected error while processing a request (e.g., a database connection failure). It responds with `500 Internal Server Error`, indicating a problem on the server side.

### 501 Not Implemented

- **Description**: The server does not support the functionality required to fulfill the request. This status code indicates that the server does not recognize the request method or feature.
- **Example**: The client requests a method that is not supported by the server (e.g., a custom method). The server responds with `501 Not Implemented`, indicating that the requested functionality is not available.

### 502 Bad Gateway

- **Description**: The server, while acting as a gateway or proxy, received an invalid response from the upstream server. This status code indicates that the server received an erroneous response from a remote server it was accessing.
- **Example**: A server acting as a gateway receives an invalid response from an upstream server (e.g., an invalid HTTP response). It responds with `502 Bad Gateway`.

### 503 Service Unavailable

- **Description**: The server is currently unable to handle the request due to temporary overloading or maintenance. This status code indicates that the server is temporarily unavailable.
- **Example**: The server is undergoing maintenance or is overloaded with requests. It responds with `503 Service Unavailable`, indicating that the service is temporarily down.

### 504 Gateway Timeout

- **Description**: The server, while acting as a gateway or proxy, did not receive a timely response from the upstream server. This status code indicates that the server timed

out while waiting for a response from a remote server.

- **Example**: A server acting as a proxy times out while waiting for a response from an upstream server (e.g., a slow external API). It responds with `504 Gateway Timeout`.
