--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#                                       WEB APPLICATION BASICS
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- Understand what a web application is and how it runs in a web browser.
- Break down the components of a URL and see how it helps access web resources.
- Learn how HTTP requests and responses work.
- Get familiar with the different types of HTTP request methods.
- Understand what different HTTP response codes mean.
- Check out how HTTP headers work and why they matter for security.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#                                       WEB APPLICATION OVERVIEW
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- web application is made up of front end and back end 

- Front end is part which users can see and interact with like HTML, CSS and javascript
    - HTML -> HYPERTEXT MARKUP LANGUAGE -> This is like basic of front end of how it looks and how its structure is to be.
    - CSS  -> CASCADING STYLE SHEET -> This is nothing but , features of the web application like font size , color  etc
    - JS -> JAVASCRIPT -> THis is how the web page intercts on users decision or clicks

- BACKEND is part which users cannnot see , but is very much necessary as it contains :
    - DATABSE -> Where users store data such as name , pass etc
    - There are many other Infrastructure components underpinning Web Applications, such as web servers, application servers, storage, various networking devices, and other software that support the web application
    - WAF (Web Application Firewall) is an optional component for web applications. It helps filter out dangerous requests away from the Web Server and provides an element of protection

1) Which component on a computer is responsible for hosting and delivering content for web applications?
-> WEB SERVER

2) Which tool is used to access and interact with web applications?
-> WEB BROWSER

3) Which component acts as a protective layer, filtering incoming traffic to block malicious attacks, and ensuring the security of the the web application?
-> WEB APPLICATION FIREWALL


--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#                                       Uniform Resource Locator
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- A Uniform Resource Locator (URL) is a web address that lets you access all kinds of online content—whether it’s a webpage, a video, a photo, or other media. It guides your browser to the right place on the Internet.

-  SCHEME ->The scheme is the protocol used to access the website
-  USER-> Some URLs can include a user’s login details (usually a username) for sites that require authentication
- DOMAIN/HOST -> The host or domain is the most important part of the URL because it tells you which website you’re accessing.
- PORT-> The port number helps direct your browser to the right service on the web server. It’s like telling the server which doorway to use for communication
- Path -> The path points to the specific file or page on the server that you’re trying to access. It’s like a roadmap that shows the browser where to go
- Query String -> The query string is the part of the URL that starts with a question mark (?). It’s often used for things like search terms or form inputs. Since users can modify these query strings, it’s important to handle them securely to prevent attacks like injections, where malicious code could be added.
- Fragment -> The fragment starts with a hash symbol (#) and helps point to a specific section of a webpage—like jumping directly to a particular heading or table.

1) Which protocol provides encrypted communication to ensure secure data transmission between a web browser and a web server?
-> HTTPS

2) What term describes the practice of registering domain names that are misspelt variations of popular websites to exploit user errors and potentially engage in fraudulent activities?
-> TYPOSQUATTING [ This is nothing but sometime the hackers use phising website which are vulnerable and can capture the targets user creds when they type and enter , is like fake websites ]

3) What part of a URL is used to pass additional information, such as search terms or form inputs, to the web server?
-> QUERY STRING


# HTTP MESSAGES

- HTTP messages are packets of data exchanged between a user (the client) and the web server. These messages are very important for understanding how web applications work because they show how users' requests and the server's responses are communicated.

- There are two types of HTTP messages:
    - HTTP Requests: Sent by the user to trigger actions on the web application.
    - HTTP Responses: Sent by the server in response to the user’s request.

- START LINE -> The start line is like the introduction of the message. It tells you what kind of message is being sent—whether it's a request from the user or a response from the server
- HEADERS -> Headers are made up of key-value pairs that provide extra information about the HTTP message. They give instructions to both the client and the server handling the request or response. These headers cover all sorts of things, like security, content types, and more, making sure everything goes smoothly in the communication.
- EMPTYP LINE -> emplty liine is a small space btw header and body , it is imp because it helps us keep the header and body seperate and not mix up the contents
- BODY -> This is where the actual data is stored for user and API for servers is stored here\


# HTTP Request: Request Line and Methods

- key parts like the method (e.g., GET or POST), path (e.g., /login), and version (e.g., HTTP/1.1). These elements make up the basics of how a client (user) communicates with a server.

### Request Line
- Example: METHOD /path HTTP/version
- The request line (or start line) is the first part of an HTTP request and tells the server what kind of request it’s dealing with. It has three main parts: the HTTP method, the URL path, and the HTTP version.

### HTTP Methods

- GET -> Used to fetch data from the server without making any changes.
- POST -> Sends data to the server, usually to create or update something
- PUT -> Replaces or updates something on the server
- DELETE -> Removes something from the server
- PATCH -> Updates part of a resource
- HEAD -> Same as GET ,  but only retrieves headers, not the full content
- OPTIONS -> Tells you what methods are available for a specific resource, helping clients understand what they can do with the server.
- TRACE -> Similar to OPTIONS, it shows which methods are allowed, often for debugging
- CONNECT -> Used to create a secure connection, like for HTTPS.

### HTTP Version

- The HTTP version shows the protocol version used to communicate between the client and server. Here’s a quick rundown of the most common ones:

1) Which HTTP protocol version became widely adopted and remains the most commonly used version for web communication, known for introducing features like persistent connections and chunked transfer encoding?
-> HTTP/1.1

2) Which HTTP request method describes the communication options for the target resource, allowing clients to determine which HTTP methods are supported by the web server?
-> OPTIONS

3) In an HTTP request, which component specifies the specific resource or endpoint on the web server that the client is requesting, typically appearing after the domain name in the URL?
-> URL PATH


# HTTP Request: Headers and Body

- Request Headers allow extra information to be conveyed to the web server about the request. Some common headers are as follows:
- 