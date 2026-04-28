# Systems as Attack Vectors

- A system can be student laptop or bank employee laptop 
- A system can be a mail or a mail server contaning lakhs of emails

- First step is `breaking system` --> Then depends on attackers motive

- Types of attacks that might happens on system :
    - `HUMAN-LED ATTACK` --> plugging unknown USB , using vulnarable sooftware, Downloading malware unknowingly etc

    - `VULNERABILITITES` --> Evry piece of software have securtiy flaw, its how the company hides or protects it 

    - `SUPPLY-CHAIN` --> Apps depends on libraries/dependencies and these dependencies might have vuln , hence making the whole app vulnerable


- If a vuln is detected in system , then we need to create a `patch` before its wxploited by attackers


- `MISCONFIGURATIONS` 
    - misconfiguration isn't a bug in the software but a mistake in how the system was set up [ BY IT TEAM ]
    - Ex:
        - using weak pass
        - unknonwingly keeping access to DB enabled


- Responding to `Misconfigurations`:
    - This cannot be fixed via updates or patch
    - This can be fixed by :
        - pentester
        - vulnerability scanning
        - configuration edits