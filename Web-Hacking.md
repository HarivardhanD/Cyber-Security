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

### REQUEST HEADER

- Request Headers allow extra information to be conveyed to the web server about the request. Some common headers are as follows:
- Some common headers are 
    - HOST -> Specifies the name of the web server the request is for.
        - Host: tryhackme.com

    - User-Agent -> Shares information about the web browser the request is coming from.
        - User-Agent: Mozilla/5.0

    - Referer -> Indicates url from which  request came from
        - Referer: https://www.google.com/

    - COOKIE -> Information the web server previously asked the web browser to store is held in cookies.
        - Cookie: user_type=student; room=introtowebapplication; room_status=in_progress

    - Content-Type	-> DESCRIBES THE FORMAT DATA IS IN 
        - Content-Type: application/json

### REQUEST BODY :

- the data is located inside the HTTP Request Body

- There are few formats such as URL ENCODED , FORM DATA, JSON , XML .

    1) URL Encoded (application/x-www-form-urlencoded)
        - A format where data is structured in pairs of key and value where (key=value). Multiple pairs are separated by an (&) symbol, such as key1=value1&key2=value2. Special characters are percent-encoded.
        - ex : name=Aleksandra&age=27&country=US
    
    2) Form Data (multipart/form-data)
        - Allows multiple data blocks to be sent where each block is separated by a boundary string. The boundary string is the defined header of the request itself. This type of formatting can be used to send binary data, such as when uploading files or images to a web server.
        - ex :  POST /upload HTTP/1.1
                Host: tryhackme.com
                User-Agent: Mozilla/5.0
                Content-Type: multipart/form-data; boundary=----WebKitFormBoundary7MA4YWxkTrZu0gW

                ----WebKitFormBoundary7MA4YWxkTrZu0gW
                Content-Disposition: form-data; name="username"

                aleksandra
                ----WebKitFormBoundary7MA4YWxkTrZu0gW
                Content-Disposition: form-data; name="profile_pic"; filename="aleksandra.jpg"
                Content-Type: image/jpeg

    3) JSON (application/json)
        - In this format, the data can be sent using the JSON (JavaScript Object Notation) structure. Data is formatted in pairs of name : value. Multiple pairs are separated by commas, all contained within curly braces { }.
        - ex :  Content-Type: application/json
                Content-Length: 62

                {
                    "name": "Aleksandra",
                    "age": 27,
                    "country": "US"
                }

    4) XML (application/xml)
        - In XML formatting, data is structured inside labels called tags, which have an opening and closing. These labels can be nested within each other. You can see in the example below the opening and closing of the tags to send details about a user called Aleksandra.
        - ex:   Content-Type: application/xml
                Content-Length: 124

                <user>
                    <name>Aleksandra</name>
                    <age>27</age>
                    <country>US</country>
                </user>

1) Which HTTP request header specifies the domain name of the web server to which the request is being sent?
-> HOST

2) What is the default content type for form submissions in an HTTP request where the data is encoded as key=value pairs in a query string format?
-> application/x-www-form-urlencoded

3) Which part of an HTTP request contains additional information like host, user agent, and content type, guiding how the web server should process the request?
-> REQUEST HEADERS


# HTTP Response: Status Line and Status Codes

- whenever u interact with web applicatiiono , u will get a feedback from the server , which includes status code and small piece of line with  the same.
- The first line in HTTP response is called status lines and it gives us status code alog with inforation , which is just small line stating the code .

- The Status Code is the number that tells you if the request succeeded or failed, while the Reason Phrase explains what happened.
    - in this we have mainly 5 catogories, lets discuss it below .
        
        1) Informational Responses (100-199)
            - These codes mean the server has received part of the request and is waiting for the rest. It’s a "keep going" signal.

        2) Successful Responses (200-299)
            - These codes mean everything worked as expected. The server processed the request and sent back the requested data.

        3) Redirection Messages (300-399)
            - These codes tell you that the resource you requested has moved to a different location, usually providing the new URL.

        4) Client Error Responses (400-499)
            - These codes indicate a problem with the request. Maybe the URL is wrong, or you’re missing some required info, like authentication.

        5) Server Error Responses (500-599)
            - These codes mean the server encountered an error while trying to fulfil the request. These are usually server-side issues and not the client’s fault.

    
- 100 (Continue)
- The server got the first part of the request and is ready for the rest.

- 200 (OK)
- The request was successful, and the server is sending back the requested resource.

- 301 (Moved Permanently)
- The resource you’re requesting has been permanently moved to a new URL. Use the new URL from now on.

- 404 (Not Found)
- The server couldn’t find the resource at the given URL. Double-check that you’ve got the right address.

- 500 (Internal Server Error)
- Something went wrong on the server’s end, and it couldn’t process your request.

1) What part of an HTTP response provides the HTTP version, status code, and a brief explanation of the response's outcome?
-> STATUS LINE

2) Which category of HTTP response codes indicates that the web server encountered an internal issue or is unable to fulfil the client's request?
-> SERVER ERROR RESPONSES

3) Which HTTP status code indicates that the requested resource could not be found on the web server?
-> 404


# HTTP Response: Headers and Body

### Response Header
- When a web server responds to an HTTP request, it includes HTTP response headers, which are basically key-value pairs
- Key headers like Content-Type, Content-Length, and Date give us important details about the response the server sends back.
    - DATE -> THIS GIVES US EXACT DATE AND TIME, WHEN THE SERVER WAS CREATED
    - CONTENT-TYPE -> THIS GIVES US THE DATA FORMAT OF THE HTTP REQUEST IF ITS JSON OR XML OR URL-ENCODED OR DATA-FORMAT
    - SERVER -> THIS GIVES US OON WHAT SERVERR IS THE PROCESS TAKING PLACE , WHICH CAN BE EASY TO DEBUG , BUT ALSO IT MIGHT BE SENSITIVE IF HACKERS GET THIS INFO.  
    - SET-COOKIE -> IT SEND COOKIES FROM SERVER TO CLINET AND CAN STORE INFORMNATION ABOUT THE CLIENT FOR FUTURE USES. MAKES SURE IT IS HTTPS AND HTTPONLY
    - CACHE-CONTROL -> This header tells the client how long it can cache the response before checking with the server again
    - LOCATION -> IF THE URL HAS BEEN CHANGES ,THEMM THIS GIVES US URL OF THE NEW WEBSITEW WHERE THE CONTENT IS AVAILABLE.

### Response Body

- The HTTP response body is where the actual data lives—things like HTML, JSON, images, etc., that the server sends back to the client. To prevent injection attacks like Cross-Site Scripting (XSS), always sanitise and escape any data (especially user-generated content) before including it in the response.

1) Which HTTP response header can reveal information about the web server's software and version, potentially exposing it to security risks if not removed?
-> server

2) Which flag should be added to cookies in the Set-Cookie HTTP response header to ensure they are only transmitted over HTTPS, protecting them from being exposed during unencrypted transmissions?
-> SECURE flag

3) Which flag should be added to cookies in the Set-Cookie HTTP response header to prevent them from being accessed via JavaScript, thereby enhancing security against XSS attacks?
-> HttpOnly

# SECURITY HEADERS

- This provides us means to secure the web application more.
- Few of security headers are below :
    - Content-Security-Policy (CSP)
    - Strict-Transport-Security (HSTS)
    - X-Content-Type-Options
    - Referrer-Policy

- You can use a site like [https://securityheaders.io/] to analyse the security headers of any website.

1) CONTENT SECURITY POLICY [ CSP ]

- This is like , is used to prrvent cross scite scrioting. Malicious code could be hosted on a separate website or domain and injected into the vulnerable website.
- CSP provides additional layer of security . A CSP provides a way for administrators to say what domains or sources are considered safe and provides a layer of mitigation to such attacks.

- Looking at an example CSP header:

    - Content-Security-Policy: default-src 'self'; script-src 'self' https://cdn.tryhackme.com; style-src 'self'

    - We see the use of:

        - default-src
            - which specifies the default policy of self, which means only the current website.

        - script-src
            - which specifics the policy for where scripts can be loaded from, which is self along with scripts hosted on https://cdn.tryhackme.com

        - style-src
            - which specifies the policy for where style CSS style sheets can be loaded from the current website (self)

2) Strict-Transport-Security (HSTS)

- The HSTS header ensures that web browsers will always connect over HTTPS.

- HSTS -> HTTP STRICT TRANSPORT SECURITY

- EX  : Strict-Transport-Security: max-age=63072000; includeSubDomains; preload
    - max-age
        - This is the expiry time in seconds for this setting

    - includeSubDomains
        - An optional setting that instructs the browser to also apply this setting to all subdomains.

    - preload
        - This optional setting allows the website to be included in preload lists. Browsers can use preload lists to enforce HSTS before even having their first visit to a website.


3) X-Content-Type-Options

- The X-Content-Type-Options header can be used to instruct browsers not to guess the MIME time of a resource but only use the Content-Type header

- MIME -> Multipurpose Internet Mail Extensions (MIME) is an Internet standard that extends the format of email messages to support text in character sets other than ASCII, as well as attachments of audio, video, images, and application programs.

- X-Content-Type-Options: nosniff
    Here’s a breakdown of the X-Content-Type-Options header by directives:

    - nosniff
        - This directive instructs the browser not to sniff or guess the MIME type.

3) Referrer-Policy

- This header controls the amount of information sent to the destination web server when a user is redirected from the source web server, such as when they click a hyperlink

- Referrer-Policy: no-referrer
- Referrer-Policy: same-origin
- Referrer-Policy: strict-origin
- Referrer-Policy: strict-origin-when-cross-origin

    - Here’s a breakdown of the Referrer-Policy header by directives:

        - no-referrer
            - This completely disables any information being sent about the referrer

        - same-origin
            - This policy will only send referrer information when the destination is part of the same origin. This is helpful when you want referrer information passed when hyperlinks are within the same website but not outside to external websites.

        - strict-origin
            - This policy only sends the referrer as the origin when the protocol stays the same. So, a referrer is sent when an HTTPS connection goes to another HTTPS connection.

        - strict-origin-when-cross-origin
            - This is similar to strict-origin except for same-origin requests, where it sends the full URL path in the origin header.

1) In a Content Security Policy (CSP) configuration, which property can be set to define where scripts can be loaded from?
-> script-src

2) When configuring the Strict-Transport-Security (HSTS) header to ensure that all subdomains of a site also use HTTPS, which directive should be included to apply the security policy to both the main domain and its subdomains?
-> InlcudeSubDomains

3) Which HTTP header directive is used to prevent browsers from interpreting files as a different MIME type than what is specified by the server, thereby mitigating content type sniffing attacks?
-> nosniff


# Practical Task: Making HTTP Requests

- SO i was given task to complete like the following :

1) Make a GET request to /api/users. What is the flag?
-> nothing complicate , i just write the following in the URL but with GET request -> https://tryhackme.com/api/users

2) Make a POST request to /api/user/2 and update the country of Bob from UK to US. What is the flag?
-> As we know post is used to update the value so we use POST
- Its like , -> https://tryhackme.com/api/user/2 and then in the setting i changes the following 
    - name : Bob
    - country : US

- Run it and hence done 

3) Make a DELETE request to /api/user/1 to delete the user. What is the flag?
-> This ones damn easy as well , just make the method DELETE and wrte the following -> https://tryhackme.com/api/user/1 


------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#                               JAVA SCRIPT ESSENTIALS
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
- JAVA SCRIPT is a very essential scripting language and is used to add interactivenss to html pages and make it responsive by inlcuding onClick button and animations.

- It is primiarly used with HTML.

## VARIABLES 
## ---------

- Variables are containers that allow you to store data values in them.

- There are three ways to declare variables in JS: `var`, `let`, and `const`. While var is function-scoped, both let, and const are block-scoped, offering better control over variable visibility within specific code blocks.


## DATA TYPES 
## -----------

- In JS, data types define the type of value a variable can hold. Examples include string (text), number, boolean (true/false), null, undefined, and object (for more complex data like arrays or objects).


## FUNCTIONS 
## ---------

- A function represents a block of code designed to perform a specific task
- Likes if we want to print a students name again and agian , instead of using print everywhere , u can create a function and then call it wherever required


## Loops
## -----

- Loops allow you to run a code block multiple times as long as a condition is true. Common loops in JS are for, while, and do...while, which are used to repeat tasks

1) What term allows you to run a code block multiple times as long as it is a condition?
-> LOOPS 


# JAVA SCRIPT OVERVIEW
# --------------------

- Java script is an interppreted language , ie  meaning the code is executed directly in the browser without prior compilation.

- Since JS is executed on client side, we can easily use it with html and run it in the web browser directly withouy any extra compliler or tool.

- Go to -> google chrome -> then either ` cntrl + Shift + I ` or right click and inspect -> then go to console and here u can execute ur js code 


# INTEGRATING JAVA SCRIPT IN HTML 
# --------------------------------

- JS is not used to render content; it works with HTML and CSS to create dynamic and interactive web pages

- There are two main ways to integrate JS into HTML: internally and externally.

### INTERNAL JS

- This is really nothing but using js code directly inside an html file
- create an .html file -> then write the following code :
    <!DOCTYPE html>
    <html lang="en">
        <head>
            <title>Internal JS</title>
        </head>
        <body>
                <h1>Addition of Two Numbers</h1>
        <p id="result"></p>

            <script>
                let x = 5;
                let y = 10;
                let result = x + y;
                document.getElementById("result").innerHTML = "The result is: " + result;
            </script>
        </body>
    </html>

- Now in this the browser will show us the following -> The result is 15 

- Here as we can see <script></script> is withing HTML file and also , as we can see <p id ="result"></p> prints the result , id = "result" calls document.getElementById("result")

### External JavaScript

- External JS involves creating and storing JS code in a separate file ending with a .js file extension. This method helps developers keep the HTML document clean and organised

- Here what we do is just use 2 files , one is .html and other is .js and in the .html , we use inside body the following code :
    < p id="result"></p>
    <!-- Link to the external JS file -->
    <script src="script.js"></script>
    
- So here we use script tag and inside than as u can see we have used `src` which means , here we are linking html to external js file


### Verifying Internal or External JS

- When pen-testing a web application, it is important to check whether the website uses internal or external JS.

- For this , we do go to chrome and open the webite and right click and choose -> view page resource and hence u can see the html code .


1) Which type of JavaScript integration places the code directly within the HTML document?
-> INTERNAL

2) Which method is better for reusing JS across multiple web pages?
-> EXTERNAL

3) What attribute links an external JS file in the <script> tag?
-> SRC


# ABUSING DIALOGUE FUNCTIONS
# --------------------------

- One of the main objectives of JS is to provide dialogue boxes for interaction with users and dynamically update content on web pages. 

- JS provides built-in functions like `alert`, `prompt`, and `confirm` to facilitate this interaction.

- These functions allow developers to display messages, gather input, and obtain user confirmation. However, if not implemented securely, attackers may exploit these features to execute attacks like Cross-Site Scripting (XSS)

### Alert

- The alert function displays a message in a dialogue box with an "OK" button, typically used to convey information or warnings to users.

- open the Chrome console, type alert("Hello THM"), and press Enter.

### Prompt

- The prompt function displays a dialogue box that asks the user for input. It returns the entered value when the user clicks "OK", or null if the user clicks "Cancel"

- For example, to ask the user for their name, we would use `prompt("What is your name?");`.

### Confirm

- The confirm function displays a dialogue box with a message and two buttons: "OK" and "Cancel". It returns true if the user clicks "OK" and false if the user clicks "Cancel".

- we would use `confirm("Are you sure?");` in the console and then it will displya in the browser -> are u sure ? Ok : cancel ; if i press cancel it return false in console and if i enter ok , return true in the console

### How Hackers Exploit the Functionality

- Lets say u get a html document , not looking sus so u opne it , but asa u open u get alert hack hack hack, maybe so many time that ur web browser will crash , yes so this is done by js , so its always recommeded to open the file / html document from trusted source 

1) Which of the JS interactive elements should be used to display a dialogue box that asks the user for input>
-> PROMPT


# BYPASSING CONTROL FLOW STATEMENT

- JS provides several control flow structures such as if-else, switch statements to make decisions, and loops like for, while, and do...while to repeat actions

### CONDITIONAL STATEMTNS

- if-else

### Bypassing Login Forms

- here nothing but we will use prompt along with if-else , so that the user should enter login and password if they want top access the file / website

# EXPLORING MINIFIED FILES 

- We know how to use js file in human readable form, but what is it is not human readable or minified ?

- Minification in JS is the process of compressing JS files by removing all unnecessary characters, such as spaces, line breaks, comments, and even shortening variable names. 

- Minification makes the code more compact so that it can be made smalled in size , but it becomes difficult to read tho executes the same functionality

- Similarly, obfuscation is often used to make JS harder to understand by adding undesired code, renaming variables and functions to meaningless names, and even inserting dummy code.

- so in general i would say obfuscation and minification is used to encode the js with gibberish code, tho same functionality to keep it protected and small in size , making it difficult to read 

- website which obfuscated -> [ https://codebeautify.org/javascript-obfuscator ].

- Deobfuscate it using -> [https://obf-io.deobfuscate.io/]


# BEST PRACTICES

### Avoid Relying on Client-Side Validation Only

- One of JS's primary functions is performing client-side validation. Developers sometimes use it for validating forms and rely entirely on it, which is not a good practice. Since a user can disable/manipulate JS on the client side, performing validation on the server side is also essential.

### Refrain from Adding Untrusted Libraries

- as we know , src is used to add .js files to html , so before adding it make sure the .js file is from trusted source

### Avoid Hardcoded Secrets

- Never hardcode sensitive data like API keys, access tokens, or credentials into your JS code


### Minify and Obfuscate Your JavaScript Code

- Minifying and obfuscating JS code reduces its size, improves load time, and makes it harder for attackers to understand the logic of the code. Therefore, always minify and obfuscate the code when using code in production

- Tho hackers can reverse engineer , tho it will take some time and effort