# CYBER KILL CHAIN

- The `Cyber Kill Chain` will help you understand and protect against ransomware attacks, security breaches as well as Advanced Persistent Threats (APTs). 
- You can use the `Cyber Kill Chain` to assess your network and system security by identifying missing security controls and closing certain security gaps based on your company's infrastructure.
- `CYBER KILL CHAIN` --> Helps us to recognize the `intrusion` attempts and understand the intruder's goals and objectives. 

- So ` CYBER KILL CHAIN` is methodology of hackers trying to attack a company .

### Reconnaissance

- Reconnaissance is the research and planning phase of an attack against a system or victim
- `PASSIVE RECON ` --> NO DIRECT INTERACTION
- `ACTIVE RECON` --> DIRECT INTERACTION 

- `Reconnaissance` is a very imp phase and it helps the attacker to knon when ,whom , where and what to attack or target.

- Some RECON tools :
    - `EMAIL HARVESTING` -->  process of obtaining email addresses from public, paid, or free services. 
        - TOOLS FOR THE PURPOSE :
            - `theHarvester`[https://github.com/laramies/theHarvester]: other than gathering emails, this tool is also capable of gathering names, subdomains, IPs, and URLs using multiple public data sources.
            - `Hunter.io`[https://hunter.io/]: this is an email hunting tool that will let you obtain contact information associated with the domain.
            - `OSINT Framework` [https://osintframework.com/]: OSINT Framework provides the collection of OSINT tools based on various categories.


### PHASE 2 --> WEADPONIZATION

- Based on the `RECON` --> attacker decides the payload / Malware / Exploits and either creates it or Buys em from `DARK WEB`

- term for automated scripts embedded  that can be used to perform tasks or exploited by attackers for malicious purposes --> ` MACRO `


### PHASE 3 --> DELIVERY

- How will attacker , infect the system 
- There are multiple ways for this , few are :
    - `Phishing emails` ( individual or grp phishing)
    - ` USB Drops `
    - ` Watering Hole attack` --> This Aim at a specific group of people by compromising the website they are usually visiting, redirecting them to a malicious website of the attacker's choice or creation

### PHASE 4 --> EXPLOITATION

- The moment , Attackers code executes on target, taking advantage of known vulnerability.


- `Malicious macro execution`: This may have been delivered through a phishing email, that would execute ransomware when the victim opens it.
- `Zero-day exploits`: These leverages on unknown and unpatched flaws in a system. These exploits leave no opportunity for detection at the beginning.
- `Known CVEs`: The attacker can choose to exploit unpatched public vulnerabilities found on the target environment.


### PHASE 5 --> INSTALLATION

- Once attacker gets access, he first installs a ` BACKDOOR` on the Target .

- This is done, so that if he is caught or he disconnects, using `BACKDOOR` he can connect back to the target.

- Backdoors can be :
    - `WEBSHELL` --> `BACKDOORS` for web server
    - Using `METERPRETER` to install a backdoor on victims machine
    - Modifying windows services, to run backdoor whenever system boots --> `Adding the entry to the "run keys" for the malicious payload `


- The attacker can also use the `Timestomping` technique, which lets an attacker modify the file's timestamps, including to modify, access, create and change times


### PHASE 6 --> COMMAND AND CONTROL

- After having control on Victims system , the attacker sets it to communicate with him, hence gaining remote access of the target system [ Called as `C&C` or ` C2 Beaconing` ]

- The most common C2 channels used by adversaries include:
    - `HTTP` on `port 80` and `HTTPS on port 443`, where this type of beaconing blends the malicious traffic with the legitimate traffic and can `help the attacker evade firewalls`.
    - `DNS (Domain Name Server)`, where the infected machine makes constant DNS requests to the DNS server that belongs to an attacker, this type of C2 communication is also known as `DNS Tunneling`


### PHASE 7 --> ACTION ON OBJECTION [ EXFILTRATION ]

- Collect the credentials from users.
- Perform privilege escalation 
- Internal reconnaissance (for example, an attacker gets to interact with internal software to find its vulnerabilities).
- Lateral movement through the company's environment.
- Collect and exfiltrate sensitive data.
- Deleting the backups and shadow copies. Shadow Copy is a Microsoft technology that can create backup copies, snapshots of computer files, or volumes. 
- Overwrite or corrupt data.


- What technology is included in Microsoft Windows that can create backup copies or snapshots of files or volumes on the computer, even when they are in use? 
    - ` SHADOW COPY `