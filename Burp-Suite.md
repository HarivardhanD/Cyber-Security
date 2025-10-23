# INTRODUCTION

- Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing.

- Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. 

- The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

- Burp suite professional -> This is the best version which has almost all the features used for web application pentesting and also used by professionals.

- Burp suite Enterprise -> This ones advantage is , it is used for scanning, yes its major power is scannig.

- We will be using  burp community additon, which tho does not have all the features, but is good for beginners and free of cost.

- Important key words, when using BURP :
    - Proxy: The Burp Proxy is the most renowned aspect of Burp Suite. It enables interception and modification of requests and responses while interacting with web applications.

    - Repeater: Another well-known feature. Repeater allows for capturing, modifying, and resending the same request multiple times.

    - Intruder: Despite rate limitations in Burp Suite Community, Intruder allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.

    - Decoder: Decoder offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target.

    - Comparer: As the name suggests, Comparer enables the comparison of two pieces of data at either the word or byte level. 

    - Sequencer: Sequencer is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. 

    - Tasks: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application.

    - Event log: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

    - Issue Activity: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

    - Advisory: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. 

## INTRODUCTION TO BURP PROXY

- The Burp Proxy is a fundamental and crucial tool within Burp Suite.

-  It enables the capture of requests and responses between the user and the target web server.

- Intercepting Requests: When requests are made through the Burp Proxy, they are intercepted and held back from reaching the target server. The requests appear in the Proxy tab, allowing for further actions such as forwarding, dropping, editing, or sending them to other Burp modules.

- To disable the intercept and allow requests to pass through the proxy without interruption, click the Intercept is on button.

-  The captured requests can be viewed in the HTTP history and WebSockets history sub-tabs

## CONNECTING THROUGH THE PROXY 

-  configuring the proxy using the FoxyProxy extension in Firefox.

- Here we will  be configuring burp suite proxy using foxyproxy

### Steps:

- Install FoxyProxy: Download and install the [https://addons.mozilla.org/en-US/firefox/addon/foxyproxy-basic/]

- u will have foxyproxy extension on ur browser top  most part.
- Make sure that ur using firefox browser, as this particular foxyproxy wont work here.

- Then click on the foxyproxy symbol and go to option.

- From options go to proxies and click ADD.
- U willl have empty column where u are required to add port no, hostname and all.
- After all of this is added , click OK/SAVE.

- Then go to burp suite -? INTECEPT -> Click intercept to ON.

- Then go to browser and search the hostname u wanna intercept the request.

- The webpage u wanna intercept wont open because intercept is on , but when u go back to burp suite u will have all the requests there by.

## Site Map and Issue Definitions

- The target tab in BURP-SUITE has three subtabs:

    - SITE-MAP : It maps all of our activities.
                Every page we visit when our proxy is on will be displayed here.
                In Burp professional, it will also map all the links btw the pages.
                It also is used to get API used  when accesing the webpages.

    - Issues definitions : It will give us all vulnerabilities scanner will look for .
                             The Issue definitions section provides an extensive list of web vulnerabilities, complete with descriptions and references.

    - Scope settings : We can include/exclude specific domains.
                        So this can be used to avoid unnecessary traffic capturing 


1) I should find a flag in browser !

- SO we have a website -> https://ls.com
- First in burp , go to target and then click scope
- First turn on intercept and click on all the links on the webbpage
- After u clicked it go back to burp -> target-> sitemap, here u will find information about all the links clicked by u and then inspect it and once u find a suspious link , u can try opening that page and u will find ur required flag


## THE BURP SUITE BROWSER

- In addition to modifying our regular web browser to work with the proxy, Burp Suite also includes a built-in Chromium browser that is pre-configured to use the proxy without any of the modifications we just had to do.

- But when u are  using burp in linux with root privilages, u wont be able to opne the browser directly from the burp suite as it will show u error regarding the same saying sandbox not availabe.

- To fix this u can do one of the following:
    - Run burp-suite in low privilage account.
    - Go to burp-> settings -> tools -> burp's browser ->  check the Allow Burp's browser to run without a 
    
- The problem with checking the burps shit is that , i can cause the attacker to have complete access to ur system, if hacked , so be caustios while checking it .

- Why is it risky??
-> Sandbox acts like a security layer btw browser and system , ie even if u visit a malicious website through sandboc, only few files will be exposed , rest of ur system will be safe, but in burp when u check to use burp browser without sandbox, what happens is it gives full access to the attacker of ur system as the security layet does not exist.


## SCOPING AND TARGETING 

- Scopiing is like , when u intercept the traffic all the data gets capture , and analysiing all network traffic can be overwhelming and unnecessary , so in order to fix this all u can do is scoping , ie, just filter out or use the traffic u wanna analyse.

- To do this , initially go to burp -> target -> subtask -> scope -> add scope -> Here put the ip address of the target u wanna research on and then all traffic u will receive iin burp will be only of this particular target website.

## Proxying HTTPS

- Sometimes using burp u can access the website with TLS .
- It says CA , ie certificate not found.
- Now to fix this we gotta do the following:
    - Download the CA Certificate : With burp proxy activated go to -> [ http://burp/cert], this will download a file called cacert.der. Save this file somewhere on your machine.

    - Access Firefox Certificate Settings : Type about:preferences into your Firefox URL bar and press Enter. This will take you to the Firefox settings page. Search the page for "certificates" and click on the View Certificates button.

    - Import the CA Certificate: In the Certificate Manager window, click on the Import button. Select the cacert.der file that you downloaded in the previous step.

    - Set Trust for the CA Certificate: In the subsequent window that appears, check the box that says "Trust this CA to identify websites" and click OK.
    
- Hence now u can access TLS based browsers


## EXAMPLE ATTACK

- Here we would be testing for cross site scripting ( XSS )

- XSS is nothig but like JS , where we can inject a code and it executes.

- There are various kinds of XSS – the type that we are using here is referred to as "Reflected" XSS, as it only affects the person making the web request.

- Now i went to the compaint/feedback of a website and we had 2 bars, one for emaill and other for query, but in email , i was not able ot use special characters like <,> etc.

- So i types the email and then submitted and caught the request iin the burp and then clicked oon the request and modifies the email in the burp to the script-> `<script>alert("Succ3ssful XSS")</script> ` and then i press ` cntrl + U ` to encode it , making it safe to send and then clicked forward .


## OUT OF TOPIC CONCEPTS 

- What is XSS (one-line)

XSS (Cross-Site Scripting) is when an attacker gets a website to run their JavaScript inside someone else’s browser. That script can act like the user and read or change what the page shows.

- The three types — super simple

    - Reflected XSS

        Think: you click a bad link.

        The attack code is in the URL or form you send, and the site immediately sends it back in the response.

        Only the person who clicked the link is affected.

    - Stored (persistent) XSS

        Think: you leave a message that contains the attack code.

        The site saves it (like a comment or profile). Later, anyone who views that page runs the code.

        Bad because many people can be hit.

    - DOM-based XSS

        Think: the page’s own JavaScript takes something from the URL or page and inserts it into the page unsafely.

        The server didn’t echo it — the browser’s scripts did. It’s all happening on the client side.


- Cross-Site Scripting (XSS) is when an attacker causes a website to run malicious JavaScript in another user’s browser. There are three main types: reflected XSS, where the attacker’s input is immediately echoed in the server’s response (usually via a crafted link) and affects only the user who clicks it; stored XSS, where the site saves the attacker input (e.g., in comments or profiles) and serves it later to other users; and DOM-based XSS, where client-side JavaScript reads data from the URL or page and writes it into the DOM unsafely, with no server echo required. To identify them: look for your test string in the immediate HTTP response (reflected), check if it’s saved and visible later (stored), or see if it appears only after browser scripts run (DOM). Always practice in a controlled environment and use proper output encoding and Content Security Policy to defend against XSS.

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

#                                   OWASP - TOP 10


----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

- OWASP -> OPEN WEB APPLICATION SECURITY

-  understanding web technologies and exploitations and provides resources and tools designed to improve the security of software applications.


## BROKEN ACCESS CONTROL

- Website have pages that are protected from regular users and only admin can see it and use, now if users can see this page then it is called " broken access control "

- Once in 2019,there was a bug where users could access the private video from the utube channel, now the conclusion for this as told by the attacker was , when ur tryig to exploit target, dont only attack the targetr, rather try attacking everything whicch links to that target. Sometimes the targert will have high ecurity, whereas the products linking to the target might have bad/lower security

- IDOR -> INSECURE DIRECTO OBJECT REFERENCE -> Access control vuln , where u can get into others account just by changing the ID.

- EXAMPLE:
    - Lets say we have to go to banking website, and we enter our credential and all and we are logged in to the required page-> [https://bank.thm/account?id=111111]

    - Now IDOR is like , what i do is , i change the id from 111111 to 222222 , lmao i got access to anotther account without even needing to enter the credentials.



## CRYPTOGRAPHIC FAILURES

- A cryptographic failure refers to any vulnerability arising from the misuse (or lack of use) of cryptographic algorithms for protecting sensitive information.

- Web applications require cryptography to provide confidentiality for their users at many levels.

- Lets say u wanna read ur email from browser, then when u are reading the email it should be that no one can read ur email or when ur accessing ur email, people even if they are capturiing ur network traffic, must not be able to read ur email , this is called " encrypting data in transit "

- Now the email, will be in the server, hence even the maintainer of server must not be able to read ur email , this is " encrypting data at rest "

- This cryptographic failure can give us sensitive data such as usrname, pass , DOB etc

### Cryptographic Failures (Supporting Material 1)

- If we have many data , the common way to store all of this data is in a DATABASE.

- DATABASE can either be a server or flat files, flat files is nothing but small database , stored on the disk of computer.

- Most of flat-files databases are " SQLite Databse " and client used for interacting with this database is " sqlite3 "

    - TO access it we use : ` sqlite3 <database-name> `
    - use ` PRAGMA table_info(customers);` to see the table information.
    - use ` SELECT * FROM customers;` to dump the information from the table

- Hence we can see the information

### Cryptographic Failures (Supporting Material 2)

- Now from database, we will get password hashes, now in order to crack these hashes, we cn use either john the ripper or crackstation.

- Copy paste the hash value in the crackstation and hence u can get the passwords if its in wordlist.

# INJECTION ATTACK 

- Injection happens when an application accidentally treats user input as instructions rather than plain data. It’s often caused by joining user text into queries or command lines, missing the separation between data and code

- There are multiple type of injection such as :
    - SQL Injection : user input lands inside a database query and can change the query’s logic

    - Command Injections : User queries land inside the operating system commands(shell)

    - Cross-Site Scripting (XSS) : user input that reaches other users’ browsers unescaped becomes executable script.

- DEFENCE for this is making sure user inputs are not interpreted as commands:
    
    - Using an allow list: when input is sent to the server, this input is compared to a list of safe inputs or characters. If the input is marked as safe, then it is processed. Otherwise, it is rejected, and the application throws an error.

    - Stripping input: If the input contains dangerous characters, these are removed before processing.


## Command Injection

- Command Injection occurs when server-side code (like PHP) in a web application makes a call to a function that interacts with the server's console directly.

- Once the attacker gets access to the command line in the servers side, then he can do literally anything.

- So to test for command injection , do the followiing :
    -  First mark all the places where u can input values
    - Then execute simple unix/windows command.
    - Most of the servers run as linux, so start with linux command 
    - LINUX -> `; echo INJ123;`, `; sleep 5;`, `; whoami;`, `; id;`, `; uname -a;`
    - WINDOWS -> `& echo INJ123 &`, `& whoami &`.
    - When u execute these command in the user input field and get any response in return , then its a command injection .

1) What strange text file is in the website's root directory?
- Here what i did was , first i wne to the url and tested all the command such as `robots.txt` `sitemap.xml`, `humans.txt` , `security.txt` , `README(.txt/.md/.html)`

- I did not find any result, them i went on and tried the gobuster, to find all of the direcotories and command is as follows:
    - ` gobuster dir -u http://domainname.com -w /usr/share/wordlists/dirb/common.txt -x php,txt,html,zip,env -t 40 -o gobuster_results.txt `

    - Where :
        - `-u` = URL of the target domain.
        - ` -w ` = WORDLISTS
        - `-x` = means add .php,.txt etc while searching dir
        - ` -t ` = number of threads to use, 40 is quiet good.
        - ` -o ` = Save ti in gobuster_results.txt

- Even this did not give me the required OUTPUT .
- Then ,what i did is went to the user input field and wrote ` ; ls ; `, booyah i got my first solutiion.

2) What user is this app running as?

- In the user input field , i wrote ` ; whoami ; `, and yup got the answrr

3) What is the user's shell set as?

- Users input field , ` cat /etc/passwd ` yeah thats all and i got the answer.
- I chose the ` sbin/nologin` - > It usually means that account is a service/system account, not a real human user.

- Later i tried on various command such as :
    - ` ;uname -a;`
    - `; ifconfig ; `

- Why use `;` before and after command? --> Before because if any command is being executed before out command , we want to seperate out command from that command 
After because , its a normal syntax to close command with ; . 