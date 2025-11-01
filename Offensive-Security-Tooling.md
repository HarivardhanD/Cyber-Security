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
 
