# SECURITY PRINCIPLES
# -------------------

- Here i learnt about few security principles , BASICS and also few basic security architecture

- CIA Triad
    - CONFIDENTIALITY -> This means , the messages must be confidential , ie should be between 2 users or between valid users , none other should be able to read it .
    - INTEGRETY -> No one should be able to alter the message. Meaning, the msg sent by sender should be received by receiver, without any modification.
    - AVAILABILITY -> The server must be available , whenever we need it 

- AUTHENTICATION -> The user who is ordering or sending msg, must be authentic.
- NON-REPUDIATION -> Means ,there must be proof that user ordered , so that he cant deny it later.

- DAD 
    - DISCLOSURE -> CONFIDENTIALITY is not maintained and anyone can see the message.
    - ALTERATION -> Integrity is not maintanined and message can be modified by 3rd party
    - DENIAL -> The serer is not being made AVAILABLE.

### Security models can bee used to protetct the confidentiality and integrity
### --------------------------------------------------------------------------

1) Bell-LaPadula Model

- This is to maintain confidentiality
- Here lower security cant read from higher security [ NO READ UP]
- Higher securit cant write to Lower security [ NO WRITE UP]
 
 2) BIBA model

- This is for integrity
- higer integrity dont read from lower integrity [ NO READ DOWN ]
- LowerIntegrit dont write to upper integrity [ NO WRITE UP]


- Its alwasy better to use multple layers of defense [ DEFENSE IN DEPTH ]



### ARCHITECTURAL PRINCIPLES

- DOMAIN SEPERTION -> Domain separation is a security principle that means keeping different areas of responsibility, authority, or functionality isolated from one another, so that a problem in one domain does not affect another.

-   LAYERING ->  using multiple, independent layers of defense so that if one control fails, others are still there to protect the system.
    - The benefit isn’t mainly “troubleshooting” — it’s about reducing the chance that a single point of failure compromises everything.

- ENCAPSULATION -> Hiding the internal workings of a system/component and exposing only what’s necessary through controlled interfaces. 

- REDUNDANCY -> Having duplicate systems, components, or backups to ensure availability if something fails.

- VIRTUALIZATION -> Using software (a hypervisor) to run multiple virtual machines (VMs) on a single physical machine.


### DESIGN PRINCIPLES

- LEAST PRIVILAGE -> Only higher authority members will be given admin access not all
- ATTACK SURFACE MINIMIZATION -> Means  , try to close unused ports and services.
- CENTRALIZED PARAMETER VALIDATION -> All input coming should be checked at single placce than scattering it, keep it organized
- CENTRALIZED GENERAL SECURITY PRINCIPLES -> Login ,signup , authenticaltion is done at one single server
- PREPARING FOR ERROR HANDLING AND EXCEPTION -> If system fails , it must not leak any information . 

- Vulnerability -> Vulnerable means susceptible to attack or damage. In information security, a vulnerability is a weakness.

- Threat -> A threat is a potential danger associated with this weakness or vulnerability.

- Risk -> The risk is concerned with the likelihood of a threat actor exploiting a vulnerability and the consequent impact on the business.