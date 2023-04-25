# Go Web Programming

- Go is simple and efficient for writing backend systems.
- Advanced set of features
- Focused in effectiveness and speed.
- Popular in *-as-Service systems

## Go In Web Applications

- Provides procedural and functional programming
- supports concurrency by default
- Modern packaging system
- Garbage Collection
- Powerful built-in standard libraries
- Crative open-source community

Provides viable alternative for developing large-scale web applications

- scalable
- modular
- maintainable
- high-performance

### Scalable

Large-scale web apps should be scalable: Should me able to increase the capacity of the application to take on a bigger volume of requests, quickly and easily.

- Vertical Scaling: Increasing the amount of CPUs or capacity in a single machine
- Horizontal Scaling: Increasing number of machines to expand capacity

Go scales well vertically, with its excellent support for concurrent Programming. A Go web application can run hundreds of thousand of *goroutines* with efficiency and performance

### Modular web Apps

Large-scale web applications should be built with components that work interchangeably. This approach allows to add, remove or modify features easily and gives flexibility. Go implements features associated with functional programming, including function types, functions as values, and closures to build more modular code.

Go is used to create _microservices_. In microservices architecture large-scale apps can be created by composing smaller independent services.

### Maintainable Web apps

Large-scale applications often needs to grow and evolve therefore you need to revisit and change the code regulary. 

Go was designed to encourage good software engineering practices. It has a clean and simple syntax that is very readable. 

- Go source code formatter (```gofmt```) standarizes teh formatting of Go code.
- Go expects documentation to evolve along with the code. The Go documentation tool (```godoc```) parses Go source code, including comments, and creates documentation in a variety of formats such as HTML and plain text.
- Testing is built into Go. ```gotest``` discovers test cases built int othe same package and runs functional and performance testing.

### High performing web applications

One of Go's design goals is to approach the performance of C, and although it has not reached this goal, the results are quite competitive. Go compiles to native code, has a great concurrency support, allows multiple requests to be processed at the same time.

## Web Applications

A web application is a computer program that resopnds to an HTTP request by a client and sends HTML back to the client in a HTTP response. The diference between a web server and a web app is probably that a web application does not simply return files; it processes the request and performs operations that are programmed int othe application.

- application: software program that interacts with a user and helps the user to perform an activiy. 
- web application: Applicaton that is deployed and used through the web.

## HTTP

HTTP is the application-level communications protocol that powers the World Wide Web, that uses the client-server computing model

- stateless
- text-based
- request-response

_Request-response_ is a basic way two computers talk to each other. The first computer send a _request_ to the second computer and the second computer _Responds_ to that request.

_Client-server_ computing model is one where the requester (client) always initiates the conversation with the resopnder (server). As the name suggests, the server provides a _service_ to the client. In HTTP, the client is also known as the _user-agent_, and is often a web browser. The server is often called _web server_

HTTP is a _stateless_ protocol. Each request from the client to the server returns a response from the server to the client, and that is all the protocol remembers. Subsequent requests to the asme server have absolutley no idea what happened before. Otherwise, connection-oriented protocols ceate a persistent chanel between the client and the server. HTTP 1.1 does persist connections to improve performance.

## HTTP Requests

HTTP is a request-response protocol so everything starts wit ha request. The HTTP Request consist of a few lines of text in the following order:

1. Request-line
2. Zero or more request headers
3. Empty line
4. Message body (optional)

```txt
GET /Protocols/rfc/2616/rfc2616.html HTTP/1.1
Host: www.w3.org
User-Agent: Mozilla/5.0
(empty line)
```

- request method (GET)
- URI (/Protocols...)
- Version (HTTP/1.1)
- Headers:
  - Host
  - User-Agent
  
### Request Methods

- GET: Tells the server to return the specified resource
- HEAD: Same as GET, except that the server must not return a message body.
- POST: Tells the server that the data in the message body should be passed to the resource identified by the URI.
- PUT: Tells the server that the data in the message body should be the resource at the given URI. If data already exists, that data is replaced. Otherwise, new resource is created at the place where the URI is.
- DELETE: Tells the server to remove the resource identified by the URI
- TRACE: Tells the server to return the requests.
- OPTIONS: Tells the server to return a list of HTTP methods that server supports.
- CONNECT: Tells the server to set up a network conection with the client. Ussing for setting up SSL tunneling, to enable HTTPS
- PATCH: Tells the server that the data in the message body modifies the resource indentified by the URI.

### Safe Request Methods

A method is considered safe if it does not change the state of the server: The server provides only information and nothing else. GET, HEAD, OPTIONS, and TRACE are safe methods.

### Idempotent Request MEthods

A method is considered _idempotent_ if the state of the server does not change the second time the method is called wit hthe same data. Safe methods by definition are considered idempotent as well.

PUT and DELETE are idempotent but not safe, because don't change the state of the server the second time they are called. PUT, with the same resource will result in the same actions being taken by the server.

POST is neither a safe nor an idempotent method because subsequent POST requests to the server result in a state change, depending on the server.

### Request Headers

- Accept: content types that are acceptable by the client as part of the HTTP response.
- Accept-Charset: character sets required from the server
- Authorization: Used to send Basic Authentication credentials to the server
- Cookie: cookies that were set by the calling server
- Content-Length
- Content-Type
- Host
- Referrer
- User-Agent

## HTTP Response

- Status line
- Response headers (optional)
- empty line
- Message Body (optional)

### Response Status Code

There are five classes of HTTP response status code, depending on the first digit of the code.

- 1XX: Informational. The server has received the request and is processing it.
- 2XX: Success. The server has received the request and has processed it successfully. Standard response is 200 OK
- 3XX: Redirection: The server has received and processed but the client needs to do more to complete the action.
- 4XX: Client ERROR: Tells the calient that there is something wrong with the request. Most widely known is 404 not found.
- 5XX: Server error: Tells the client that there is something wrong with the request but it is the server's fault. Generic status code is 500 internal server error.


### Response Haders

- Allow: Tells the client which request methods are supported by the server
- Contnt-Length: Length of the resopnse body in octets
- Content-Type: The content type of the response body
- Date: Curent time in GMT
- Location: Used with redirection to tell the client where to request the next URL
- Server: Domain name of the server that is returning the resonse
- Set-Cookie: Sets a cookie at the client.
- WWW-Authenticate: Tells header the client what type of authorization clients should supply in their Authorization request header.

## HTTP/2

HTTP/2 is a version of HTTP focuses on performance. Improves communications of the protocol. HTTP semantics as methods, status codes are not changed.

### Handler

a _Handler_ receives and processes the HTTP request sent from the client. Also calls the te plate engine to generate the HTML and finally bundles data into the HTTP response. In the MVC pattern the handler is the controller, but also the model. In an ideal MVC pattern implementation, the controller would be thin, with only routing and HTTP message unpacking and packing logic.

### Model-View-Controller Pattern

The MVC pattern is a popular pattern for writing web applications. So popular that it is somethimes mistaken as the web application development model itself.

Divides a programing into model, view and controller

- model: representation of the underlying data
- view: visualization of the model for the user
- controller: uses input from the user to modify the model.

It became popular for web applications