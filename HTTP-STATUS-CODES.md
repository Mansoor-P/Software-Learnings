# HTTP Status Codes Explained

HTTP status codes are issued by a server in response to a client's request made to the server. They help in identifying the outcome of the request. Below is an overview of some common HTTP status codes:

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
These status codes indicate a provisional response. The client should be prepared to receive one or more 1xx responses before receiving a regular response.

### 100 Continue
The server has received the request headers, and the client should proceed to send the request body.

### 101 Switching Protocols
The server acknowledges a request to switch protocols as indicated by the client.

## Successful Responses (2xx)
These status codes indicate that the client's request was successfully received, understood, and accepted.

### 200 OK
The request was successful, and the server has returned the requested data.

### 201 Created
The request has been fulfilled, resulting in the creation of a new resource.

### 204 No Content
The server successfully processed the request, but there is no content to return.
