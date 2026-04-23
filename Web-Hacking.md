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






----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
#                       SQL Fundamentals
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- databases are ubiquitous, it is important to understand them

# DATABASES 101

- Databases are an organised collection of structured information or data that is easily accessible and can be manipulated or analysed

- Data bases is nothing but collecetion of data such as login credentials , images , posts , watch history etc


## TYPES OF DATABASE

- There are many types of database, but lets focus here on 2 primary ones
    - RELATIONAL [ SQL]
    - NON RELATIONAL [ NOSQL ]

- RELATIONAL -> Store structured data, meaning the data inserted into this database follows a structure, Tabular format.
        ex : USN , EMAIL_ID , PASSWORD etc

- NON-RELATIONAL -> : Instead of storing data the above way, store data in a non-tabular format
        ex: social media platforms collecting user-generated content.

## Tables, Rows and Columns

- These are applicable for relational databses, since relational database has tabular format.

- All data stored in a relational database will be stored in a table. Lets create a table called 'book'

- When creating this table, you would need to define what pieces of information are needed to define a book record, for example, “id”, “Name”, and “Published_date”. These would then be your columns.

- And whatever u add , the id , name of book and date it was publishes, below each of the column, is row


## Primary and Foreign Keys

- This helps us establish relationship between tables in relational database.

- See when we are creating a table , we will require to fetch the data, and each book will be unique, so in order to get the book we want, we assign primary key to each of the books, ie a unique key which represents the particular book .
- Primary keys are unique identifier and dont repeat.

- Foreign key is used to establish a relationship btw 2 different table .

ex:  A foreign key is a column (or columns) in a table that also exists in another table within the database, and therefore provides a link between the two tables. In our example, think about adding an “author_id” field to our “Books” table; this would then act as a foreign key because the author_id in our Books table corresponds to the “id” column in the author table. Foreign keys are what allow the relationships between different tables in relational databases. Note that there can be more than one foreign key column in a table

1) What type of database should you consider using if the data you're going to be storing will vary greatly in its format?
-> NON RELATIONAL

2) What type of database should you consider using if the data you're going to be storing will reliably be in the same structured format?
-> RELATIONAL

3) Which type of key provides a link from one table to another?
-> FOREIGN KEY

4) which type of key ensures a record is unique within a table?
-> PRIMARY KEY

# SQL

- The interaction between the end user and the database can be done using SQL (Structured Query Language). SQL is a programming language that can be used to query, define and manipulate the data stored in a relational database. 

1) What serves as an interface between a database and an end user?
-> DBMS

2) What query language can be used to interact with a relational database?
-> SQL

# DATABASE AND TABLE STATEMENTS

- COMMANDS FOR SQL

- TO create a database in SQL -> ` CREATE DATABASE DATABASE_NAME ; `

- To show databases -> ` SHOW DATABASES `

- To use database / select the database ->  ` use database_name ; `

- To deleted a database we use -> ` drop database database_name ; `

- Now to create a  table withing database, we first do the following command to select the databse we created or we want to create table in using -> ` use database_name `.

- Now creating a table -> 

    CREATE TABLE example_table_name (
        example_column1 data_type,
        example_column2 data_type,
        example_column3 data_type
    );

- The aboive is general example :

    - CREATE TABLE book_inventory (
        book_id INT AUTO_INCREMENT PRIMARY KEY,
        book_name VARCHAR(255) NOT NULL,
        publication_date DATE
    );

    - Here, we create a table called book_inventory.
    - Them we add columns to it named book_id, book_name and publication_date.
    - Then we add datatypes for each column name such as INT, VARCHA.
    - AUTO_INCREMENT is present, meaning the first book inserted would be assigned book_id 1, the second book inserted would be assigned a book_id of 2, and so on
    - PRIMARY KEY Is the unique identifier assigned to each of the book.
    - VARCHAR(255)-> it can have character ie STRINGS, upto 255 length .
    - NOT NULL-> means we cannot leave the book_name empty.( should not be null ).
    - for publication_data, the datatype set is DATE

- TO see the tables in our database -> ` show tables ; `

- If we want to know what columns are contained within a table (and their data type), we can describe them using the DESCRIBE command (which can also be abbreviated to DESC)-> ` DESCRIBE table_name ;`

- Lets say i wanna add smth to my tablt, this can be done using alter 
    ex: Lets say I want to have a column in our book inventory that has the page count for each book.
    ALTER TABLE book_inventory
        ADD page_count INT;

- Similar to removing a database, you can also remove tables using the DROP statement-> ` DROP table table_name `



# CRUD OPERATIONS.

- CRUD stands for Create, Read, Update, and Delete, which are considered the basic operations in any system that manages data.

- COMMANDS MYSQL

- The Create operation will create new records in a table. In MySQL, this can be achieved by using the statement `INSERT INTO`
    ex: INSERT INTO books (id, name, published_date, description)
    VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");

- The Read operation, as the name suggests, is used to read or retrieve information from a table
    - `SELECT *`
    ex: SELECT * FROM books;

    ex2: SELECT name, description FROM books; [ if u wanan retriive only name, description]

- The Update operation modifies an existing record within a table, and the same statement, `UPDATE`.
    - UPDATE books
    SET description = "An In-Depth Guide to Android's Security Architecture."
    WHERE id = 1;

    - `SET` Clause is used to set the new value for selected column[description in our case].
    - `WHERE` is used to tell which id to update.

- The delete operation removes records from a table. We can achieve this with the `DELETE` statement.
    ex:  DELETE FROM books WHERE id = 1;

    - FROM clause, which allows us to specify the table where the record will be removed
    -  WHERE clause that indicates that it should be the one where the id is 1.

- Create (INSERT statement) - Adds a new record to the table.
- Read (SELECT statement) - Retrieves record from the table.
- Update (UPDATE statement) - Modifies existing data in the table.
- Delete (DELETE statement) - Removes record from the table.


# CLAUSES

- A clause is a part of a statement that specifies the criteria of the data being manipulated, usually by an initial statement. Clauses can help us define the type of data and how it should be retrieved or sorted. 

### DISTINCT
- The `DISTINCT` clause is used to avoid duplicate records when doing a query, returning only unique values.
    ex: if we do `select* from boosk; `, all the rows will eb dispplayed, irresepective of its repeated or no

    - But when we use ` disctinct` keyword.
    ex :  `SELECT DISTINCT name FROM books;`
    - This gives us only unique values; 

### GROUP BY Clause

- The `GROUP BY clause` aggregates data from multiple records and groups the query results in columns.
    ex: 
    SELECT name, COUNT(*)
    FROM books
    GROUP BY name;

    - selects name and counts it from the table books, and it groups it based on count

    - Before GROUP BY: | Category | Product | |----------|-----------| | Fruit | Apple | | Fruit | Banana | | Veggie | Carrot | | Veggie | Broccoli |

    SQL Query: SELECT Category, Product FROM Products;

    After GROUP BY: | Category | Count | |----------|-------| | Fruit | 2 | | Veggie | 2 |

    SQL Query: SELECT Category, COUNT(Product) FROM Products GROUP BY Category;

### ORDER BY Clause

- ascending/descneding order ( sort it )

- Using functions like `ASC` and `DESC` can help us to accomplish that

    ex : SELECT *
        FROM books
        ORDER BY published_date DESC;
    - This will set the books in descending order based on published_dates

    ex 2:  SELECT *
            FROM books
            ORDER BY published_date ASC;

### HAVING Clause

- The HAVING clause is used with other clauses to filter groups or results of records based on a condition

- SELECT name, COUNT(*)
    FROM books
    GROUP BY name
    HAVING name LIKE '%Hack%';

    - This will return us values with letter hack, as it is specified iin `having` clause 

# OPERATORS

- When working with SQL and dealing with logic and comparisons, operators are our way to filter and manipulate data effectively.

- LOGICAL operators test the truth of a condition and return a boolean value of TRUE or FALSE

### LIKE Operator

- The LIKE operator is commonly used in conjunction with clauses like WHERE in order to filter for specific patterns within a column. 
    ex: 
    SELECT *
    FROM books
    WHERE description LIKE "%guide%";

    - The query above returns a list of records from the books filtered, but the ones using the WHERE clause that contains the word guide by using the LIKE operator.

### AND Operator

- The AND operator uses multiple conditions within a query and returns TRUE if all of them are true.

- Even if one is false, it reutrns false

    ex: SELECT *
    FROM books
    WHERE category = "Offensive Security" AND name = "Bug Bounty Bootcamp"; 

    - The query above returns the book with the name Bug Bounty Bootcamp, which is under the category of Offensive Security.

### OR OPERATOR

- The OR operator combines multiple conditions within queries and returns TRUE if at least one of these conditions is true.

- If one is true and all other are false, then also it returns true.

    ex: SELECT *
    FROM books
    WHERE name LIKE "%Android%" OR name LIKE "%iOS%"; 

    - The query above returns books whose names include either Android or IOS.

### NOT Operator

- The NOT operator reverses the value of a boolean operator, allowing us to exclude a specific condition.

    ex:  SELECT *
    FROM books
    WHERE NOT description LIKE "%guide%";

    - The query above returns results where the description does not contain the word guide.


### BETWEEN Operator

- The BETWEEN operator allows us to test if a value exists within a defined range.

    EX:
    SELECT *
    FROM books
    WHERE id BETWEEN 2 AND 4;

    - it will see if there exist books btw id 2 and 4

## Comparison Operators

### EQUAL TO OPERATOR

- The = (Equal) operator compares two expressions and determines if they are equal, or it can check if a value matches another one in a specific column.

    ex: SELECT *
    FROM books
    WHERE name = "Designing Secure Software";

    - The query above returns the book with the exact name Designing Secure Software.

### Not Equal To Operator

- he != (not equal) operator compares expressions and tests if they are not equal; it also checks if a value differs from the one within a column

     ex: SELECT *
    FROM books
    WHERE category != "Offensive Security";

    - The query above returns books except those whose category is Offensive Security.

### Less Than Operator

- The < (less than) operator compares if the expression with a given value is lesser than the provided one.

    ex: SELECT *
    FROM books
    WHERE published_date < "2020-01-01";

    - The query above returns books that were published before January 1, 2020.

### Greater Than Operator

- The > (greater than) operator compares if the expression with a given value is greater than the provided one.

    ex: SELECT *
    FROM books
    WHERE published_date > "2020-01-01";

    - The query above returns books published after January 1, 2020.


### Less Than or Equal To and Greater  Than or Equal To Operators

- The <= (Less than or equal) operator compares if the expression with a given value is less than or equal to the provided on

    ex: SELECT *
    FROM books
    WHERE published_date <= "2021-11-15";

    - The query above returns books published on or before November 15, 2021.



- The >= (Greater than or Equal) operator compares if the expression with a given value is greater than or equal to the provided one

    ex: SELECT *
    FROM books
    WHERE published_date >= "2021-11-02";

    - The query above returns books that were published on or after November 2, 2021.




# Functions

### String Functions

- Strings functions perform operations on a string, returning a value associated with it.

### CONCAT() Function

- This function is used to add two or more strings together. It is useful to combine text from different columns.
    ex: SELECT CONCAT(name, " is a type of ", category, " book.") AS book_info FROM books;

    - This query concatenates the name and category columns from the books table into a single one named book_info.


### GROUP_CONCAT() Function

- This function can help us to concatenate data from multiple rows into one field. Let's explore an example of its usage.

    ex: SELECT category, GROUP_CONCAT(name SEPARATOR ", ") AS books
    FROM books
    GROUP BY category;
- The query above groups the books by category and concatenates the titles of books within each category into a single string.


### SUBSTRING() Function

- This function will retrieve a substring from a string within a query, starting at a determined position. The length of this substring can also be specified.
    ex: SELECT SUBSTRING(published_date, 1, 4) AS published_year FROM books;

    - In the query above, we can observe how it extracts the first four characters from the published_date column and stores them in the published_year column

### LENGTH() Function

- This function returns the number of characters in a string. This includes spaces and punctuation.
    ex: 
    SELECT LENGTH(name) AS name_length FROM books;

    - The query calculates the length of the string within the name column and stores it in a column named name_length.

## Aggregate Functions


### COUNT() Function

- This function returns the number of records within an expression.

    ex: SELECT COUNT(*) AS total_books FROM books;

    - counts the total number of rows in the books table and stores in total_books

### SUM() Function

- This function sums all values (not NULL) of a determined column.

    ex:  SELECT SUM(price) AS total_price FROM books;

    -  calculates the total sum of the price column and stores it in total_price.

### MAX() Function

- This function calculates the maximum value within a provided column in an expression.

    ex:  SELECT MAX(published_date) AS latest_book FROM books;

    - retrieves the latest publication (maximum value) date from the books table and stores in latest_books [ max is selected based on published date]

### MIN() Function

- This function calculates the minimum value within a provided column in an expression.

    ex:  SELECT MIN(published_date) AS earliest_book FROM books;

    - retrieves the earliest publication (minimum value) date from the books table and stores in latest_books [ min is selected based on published date]






