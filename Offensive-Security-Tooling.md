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