# PYRAMID OF PAIN

- The Pyramid of Pain is a cybersecurity model that explains:
    - How difficult it is for attackers when defenders detect/block different things.
    - It helps defenders understand:
        - what to detect
        - what gives maximum defensive value
        - what causes the most “pain” to attackers


- The below represents how difficult it is for an attacker to change the following WRT `COST` and `TIME-TAKEN` :
    - TTPs                ← hardest to change
    - Tools
    - Network Artifacts
    - Domain Names
    - Host Artifacts
    - IP Addresses
    - Hash Values         ← easiest to change
### HASH VALUES 

- Hashing a file gives us a unique hash-value , which can be used to identify malicious files ( comparing hash value against each other)
- Hashing is one side 

- Some of hashing algoroithm :
    - MD 5 --> 128 BIT VALUE --> NOT SECURE
    - SHA-1 --> 160 BIT HASH VALUE --> NOT SECURE
    - SHA-2 --> SHA - 256 ( VARIANT OF SHA-2) --> 256 BIT HASH VALUE --> CONSIDERED SECURE

- Online tools can be used to do hash lookups like [https://www.virustotal.com/gui/]--> `VIRUS TOTAL` and [https://metadefender.opswat.com/?lang=en] --> `Metadefender Cloud - OPSWAT`. 



### IP ADDRESS 

- INTERNET PROTOCOL ADDRESS 
- IDENTIFY CONNECTED DEVICES IN A NETWORK
- IPV4 --> 2^32 bit address space
- IPV6 --> 2"128 bit address space


- Security teams use IP addresses to:
    - identify malicious systems
    - track attackers
    - block malicious traffic
    - stop phishing or malware servers

- But then there is something called ` FAST FLUX` 

- Fast Flux is a DNS-based evasion technique where:
    - one malicious domain rapidly changes between many IP addresses
    - These IPs usually belong to:
        - infected computers (bots)
        - compromised systems in a botnet

- AN ATTACKER WITHOUT FAST FLUX --> ATTACKER --> IP --> WEBSITE 
    - ANALYST CHECKS THE IP AND BLOCKS
    - ATTACKER BLOCKED

- AN ATTACKER WITH `FAST FLUX` --> ATTACKER --> MANY NO. OF INFECTED BOTS WITH IP MULTIPLE IP ADDRESS --> ATTACKER BLOCK ONE IP , BUT THE OTHER BOTS KEEP ATTACKING THE WEBSITE


### DOMAIN NAMES 

- MAPPING `NAMES` TO `IP_ADDRESS`

- Attackers modify the domain name and also shorten the URL :
    - Modify Domain Name --> ADDIDAS.COM [ ORIGINAL] --> ADDlDAS.COM [ MODIFIED]
    - They use `byt.url` to modify the url

-  Attacker uses Unicode characters in the domain name to imitate the a known domain --> Called `PUNYCODE ATTACK`


### HOST ARTIFACTS

- Host artifacts are the traces or observables that attackers leave on the system, such as registry values, suspicious process execution, attack patterns or IOCs (Indicators of Compromise), files dropped by malicious applications, or anything exclusive to the current threat.


### NETWORK ARTIFACTS

- Network Artifacts also belong to the yellow zone in the Pyramid of Pain. 
- This means if you can detect and respond to the threat, the attacker would need more time to go back and change his tactics or modify the tools, which gives you more time to respond and detect the upcoming threats or remediate the existing ones.

- Network artifacts can be detected in `PCAPs (file that contains the network packet dumps)` by using a tool such as `Wireshark `or `TShark`, or exploring `IDS` (Intrusion Detection System) alerts from a tool such as `Snort`


- What is a User-Agent?
    - When a device sends an HTTP request to a server, it includes information about itself.
    - Example:
        - User-Agent: Mozilla/5.0 Chrome/120
        - This tells the server:
            - browser type
            - operating system
            - application making the request.


### TOOLS

- `MALWARE` Often drops into temp folder

- TOOLS Used by defenders against attacker :
    - ` ANTIVIRUS SIGNATURES` --> Antivirus compares files against known malware signatures.
    - `YARA Rules` -->  Malware pattern matching
    - `Detection Rules` --> 
        - SOC teams create rules to detect:
            - suspicious behavior
            - malware execution
            - malicious traffic
            - exploitation attempts

        - Used in:
            - SIEM
            - IDS/IPS
            - EDR/XDR systems

    - `MalwareBazaar & MalShare` -->
        - These are malware sample repositories.
        - Security researchers use them to:
            - download malware samples
            - analyze threats
            - create detection signatures
            - study attacker behavior

    - `Fuzzy Hashing` --> `SSDeep` is a fuzzy hashing tool.
        - `NORMAL HASHING` --> Comparing if 2 hash files are same
        - Now hackers slighly modif the code to avoid detection
        - `FUZZY HASHING` --> Checks for slight similarity rather than exact similarity


### TTP

- TTP --> `TACTICS`, `TECHNIQUES` AND `PROCEDURES`

- Here the defenders now know the `attackers goals`, their `techniques to achieve the goal` and ` Procedures`

- Hence now it is more easier for the defenders to catch the attackers .
- In this case the attacker has to either :
    - `CHANGE HIS PLAN`
    - OR
    - `CHANGE HIS TARGET`