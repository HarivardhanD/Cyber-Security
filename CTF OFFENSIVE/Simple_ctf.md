# SIMPLE CTF 

- This one was like i would ay not too tough ,, but as a beginner was quite challenging.

1) How many services are running under port 1000?
=> simple command  => ` nmap -p 1-1000 -sV ip_target `

2) What is running on the higher port?
=> SSH was running 

3) What's the CVE you're using against the application?
-> For this i did these many steps :
- First i went to the webpage , becasue i saw http was being used, hence this made me know we have a webpage
- went to the webpage, it was apache, nothing much
- then i used gobuster to discover the directories as follows : `  gobuster dir -u target_url -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r `
- I got a `/simple`
- Then , i went to ` website_url/simple `
- After this , i saw down that it said was using `CMS MADE SIMPLE VER 2.8.8 `, dk exact version
- Then, i went to web-browser adn then googled : `CMS MADE SIMPLE VER 2.8.8 `, and i found it had SQLI vuln
- YUP GOT THE ANSSWER => CVE-2019-9053

4) To what kind of vulnerability is the application vulnerable?
=> SQLi

5) What's the password?
=> Finding the pass :
- I know thst vuln is => SQLi
- I dowloaded the python script for exploiting the vuln , ie `exploit.py `
- Then, i went to terminal, to dir of ` explot.py` and then did ` cat exploit.py `
- i did the cat, so that i can see how to use the command and what flags to include and then it told me to include a wordlist and also the target url 
- Hence the commadn i used is ` python exploit.py  -u http://target_ip/simple -w path/to/wordlist `
    - Hence i got the usn and pss as follows : `Mitch` is USN and `secret` was pass

6) Where can you login with the details obtained?
=> since i knew , SSH was opne, we can login through SSH .

7) What's the user flag?
=> For this i first had to get into system as mitch :
- IN terminal , i wrote the command as follows ` ssh mitch@target_IP -p 2222 `
- This asked me pass and i wrote => ` secret ` , hecne i was in as mitch
- G00d j0b, keep up! => is the flag

8) Is there any other user in the home directory? What's its name?
=> just went to / and did ls , found the answer => sunbath

9) What can you leverage to spawn a privileged shell?
=> cracking the knucles, time to take root privilage, so what is did was first see if mitch had any root access => `sudo -l `
- gave me the output => /usr/bin/vim without a password [ meaing mitch can run vim without pass]
- GTFOBins is a curated list of binaries (like vim, less, awk, perl, etc.) and how they can be abused to get a shell or escalate privileges if they’re allowed in sudoers

- Now using ` vim ` , i could get the privilage as root ! HOW ? -> Yes, vim is a text editor, but it’s also a featureful program. It can:

    - execute shell commands from inside the editor (e.g., :!command),

    - open an interactive shell, or

    - run commands via its scripting/command interface

- When you run vim as root (because sudo allows it), using one of those features will execute the command with root privileges. In other words, the editor becomes a way to escape into a root shell.

- Then i wrote the command => ` sudo vim -c: '!/bin/sh' ` and therefore , i got the privilahe !

- WHAT IS =>  ` sudo vim -c: '!/bin/sh' ` => vim is started with root privileges because of sudo.
Vim executes :!/bin/sh, which spawns a /bin/sh shell. That shell inherits the privileges of the parent process — so it runs as root.

10) What's the root flag?
-> USING linux command, i travelled to root and got the flag => W3ll d0n3. You made it!
