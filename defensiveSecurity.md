# SOC FUNDAMENTALS

================================================================================================================================================================================================================================================================================================


## INTRODUCTION

- with the increasing use of internet, the collection of data is also increased and it is very much important to keep these data secure , so that no malicious attacker can gain access to it, as it is very much confidential.
- So in order to protect the data 24*7 hrs, SOC comes into pic.
- A SOC (Security Operations Center) is a dedicated facility operated by a specialized security team


## PURPOSE AND COMPONENTS

- The main focus of the SOC team is to keep Detection and Response intact.
- The SOC team has some resources available in the form of security solutions that help them achieve this.
- Continuous monitoring is required to detect and respond to any security incident.

### Detection
- Detect vulnerabilities => BUGS THAT ARE PRESENT IN SOFTWARE WHICH CAN BE EXPLOITED
- Detect unauthorized activity => THIS IS LIKE HACKER LOGS IN AS ADMIN . CAN BE DETECTED USING GEOGRAPHICAL LOCATIONS
- Detect policy violations => COMPANY HAS SPECIFIC SECURITY RULES AND SOC MAKES SURE THESE ARE NOT VIOLATED
- Detect intrusions => HACKERS GETTING INTO OUR SYSTEM


### RESPONSE

- Support with the incident response => Once an incident is detected, certain steps are taken to respond to it. This response includes minimizing its impact and performing the root cause analysis of the incident. The SOC team also helps the incident response team carry out these steps.

- There are three pillars of SOC :
    - PEOPLE
    - PROCESS
    - TECHNOLOGY

1) The SOC team discovers an unauthorized user is trying to log in to an account. Which capability of SOC is this?
=> DETECTION

2) What are the three pillars of a SOC?
=> PEOPLE, PROCESS , TECHNOLOGY


## PEOPLE

- In a SOC, with security solutions in place without human intervention, you'll end up focusing on more irrelevant issues.

- There are always the People who help the security solution to identify truly harmful activities and enable a prompt response.

- The People are known as the SOC team. 

- This team has the following roles and responsibilities:
    - SOC Analyst (Level 1): THEY ARE LAYER 1 DETECTORS AND CHECK IF A SPECIFIC DETECTION IS HARMFUL .
    - SOC Analyst (Level 2): SOME DETECTION MIGHT REQUIRE IN DEPTH ANALYSIS , AND THID IS DONE BY LEVEL2 ANALYST
    - SOC Analyst (Level 3):THESE ARE EXPERIENCED PLAYERS. CRITICAL PROBLEMS IDENTIFIED BY LEVEL1 AND 2, NEED RESPONSE AND RECOVERY AND THIS IS DONE BY LEVEL3 ANALYST

    - Security Engineer: All analysts work on security solutions. These solutions need deployment and configuration. Security Engineers deploy and configure these security solutions to ensure their smooth operation.

    - Detection Engineer: Security rules are the logic built behind security solutions to detect harmful activities. Level 2 and 3 Analysts often create these rules, while the SOC team can sometimes also utilize the detection engineer role independently for this responsibility.

    - SOC Manager:  THEY PROVIDE SUPPORT TO ALL OTHER LEVEL's OF SOC AND THEY PROVIDE UPDATE TO CISO(CHIEF INFORMATION SECURITY OFFICER) REGARDING THE UPDATES OF SOC EFFORT TOWARDS SECURITY


1) Alert triage and reporting is the responsibility of?
=> SOC ANALYST LEVEL 1

2) Which role in the SOC team allows you to work dedicatedly on establishing rules for alerting security solutions?
=> DETECTION ENGINEER



## PROCESS

- As we saw , in SOC there are multiple roles and each role has each PROCESS

- LETS DISCUSS SOME IMP PROCESS :

### ALERT TRIAGE

- The alert triage is the basis of the SOC team.
- The first response to any alert is to perform the triage
- The triage is focused on analyzing the specific alert.
- This determines the severity of the alert and helps us prioritize it. 
- The alert triage is all about answering the 5 Ws. What are these 5 Ws?

- Following are some questions that need to be answered during the triage of an alert. 
Alert: Malware detected on Host: GEORGE PC

- THE 5W's ARE AS FOLLOWS :
    
    - What?	=> A malicious file was detected on one of the hosts inside the organization’s network.
    - When?	=> DATE AND TIME OF WHEN THE FILE WAS DETECTED
    - Where? => The file was detected in the directory of the host: "GEORGE PC".
    - Who?	=> THE FILE WAS DETECTED FOR THE USER GEORGE
    - Why?	=> After the investigation, it was found that the file was downloaded from a pirated software-selling website. The investigation with the user revealed that they downloaded the file as they wanted to use a software for free.


### Reporting

- The detected harmful alerts need to be escalated to higher-level analysts for a timely response and resolution. 
- The report should discuss all the 5 Ws along with a thorough analysis, and screenshots should be used as evidence of the activity.


### Incident Response and Forensics

- Sometimes, the reported detections point to highly malicious activities that are critical. In these scenarios, high-level teams initiate an incident response



1) At the end of the investigation, the SOC team found that John had attempted to steal the system's data. Which 'W' from the 5 Ws does this answer?
=> WHO ?

2) The SOC team detected a large amount of data exfiltration. Which 'W' from the 5 Ws does this answer?
=> What ?




## TECHNOLOGY

- Having the right People and Processes in place would never be enough without security solutions for detection and response. 

- The Technology portion in the SOC pillars refers to the security solutions.

- These security solutions efficiently minimize the SOC team's manual effort to detect and respond to threats.

- LETS DISCUSS SOME OF THESE SECURITY SOLUTIONS:

    - SIEM(SECURITY INFORMATION AND EVENT MANAGEMENT) :
        - (SIEM) is a popular tool used in almost every SOC environment.
        - collects logs from various network devices, referred to as log sources
        - Detection rules are configured in the SIEM solution, which contains logic to identify suspicious activity
        - Modern SIEM solutions surpass this rule based detection analysis, providing us with user behavior analytics and threat intelligence capability

    - Note: The SIEM solution only provides the Detection capabilities in a SOC environment.

    - EDR ( END POINT DETECTION AND RESPONSE) :
        - (EDR) provides the SOC team with detailed real-time and historical visibility of the devices’ activities
    
    - Firewall:
        - A firewall functions purely for network security and acts as a barrier between your internal and external networks (such as the Internet). 
        - It monitors incoming and outgoing network traffic and filters any unauthorized traffic.
        - The firewall also has some detection rules deployed, which help us identify and block suspicious traffic before it reaches the internal network.



1) Which security solution monitors the incoming and outgoing traffic of the network?
=> FIREWALL

2) Do SIEM solutions primarily focus on detecting and alerting about security incidents? (yea/nay)
=> YEAH





================================================================================================================================================================================================================================================================================================
#                                           DIGITAL FORENSICS FUNDAMENTALS

================================================================================================================================================================================================================================================================================================

## INTRODUCTION

- Forensics is the application of methods and procedures to investigate and solve crimes
- The branch of forensics that investigates cyber crimes is known as digital forensics
- Cyber crime is any criminal activity conducted on or using a digital device.

1) Which team was handed the case by law enforcement?
=> DIGITAL FORENSICS



## Digital Forensics Methodology

- NIST ( NATIONAL INSTITUTE OF STANDARDS AND TECHNOLOGY)

- The NIST works on defining frameworks for different areas of technology, including cyber security, where they introduce the process of digital forensics in four phases :
    - Collection : ALL THE DEVICES AT THE CRIME SPOT NEED TO BE TAKEN IN CUSTODY , AND HANDLED CAREFULLY SO THAT DIGITAL EVIDENCE IS NOT TAMPERED

    - Examination : THE DATA COLLECTED HAS TO BE EXMAINED , BUT MIGHT ME OVERWHEL,ING, SO WE SHOULD ONLY USE THE / EXAMINE THE NECESSARY DATA

    - Analysis : THE INVESTIGATORE HAS TO ANALYZE THE AQUIRED DATA AND SEE HOW IT RELATED TO THE CRIME SCENE

    - Reporting: THIS IS LAST PHASE WHERE THE REPORT IS PREPARED BASED ON THE INVESTGATION DONE AND PRESENTED INFRONT OF LAW


- MULTIPLE TYPES OF DIGITAL FORENSICS ARE THERE SUCH AS :
    
    - Computer forensics: The most common type of digital forensics is computer forensics, which concerns investigating computers, the devices most commonly used in crimes.

    - Mobile forensics

    - Network forensics

    - Database forensics

    - Cloud forensics

    - Email forensics

1) Which phase of digital forensics is concerned with extracting the data of interest from the collected evidence?
=> EXAMINATION

2) Which phase of digital forensics is concerned with correlating the collected data to draw any conclusions from it?
=> ANALYSIS



## Evidence Acquisition

- EVIDENCE ACQUISION is a critical job as evidence must not be tampered

- THERE are few methods used while collecting the devices :

    - Proper Authorizatioz : LAW SHOULD PERMIT US TO TAKE IN CUSTODY THE DEVICES TO INVESTIGATE
    - CHAIN OF CUSTODY : LETS SAY INVESTIGATORS COLLECTED THE EVIDENCE AND AFTER FEW DAYS IT GOES MISSING, SO NO INDIVIDUAL CAN BE BLAMED HERE.
    TO SAFEGUARD THE DEVICES FROM BEING TAMPERED , WE HAVE TO DO A REPORT OF THE FOLLOWING :
    
        Description of the evidence (name, type).
        Name of individuals who collected the evidence.
        Date and time of evidence collection.
        Storage location of each piece of evidence.
        Access times and the individual record who accessed the evidence.

    - USE OF WRITE BLOCKERS : 
        Suppose you are collecting evidence from a suspect’s hard drive and attaching the hard drive to the forensic workstation.
        While the collection occurs, some background tasks in the forensic workstation may alter the timestamps of the files on the hard drive. This can cause hindrances during the analysis, ultimately producing incorrect results.
        If we use write blockers,  the suspect’s hard drive would remain in its original state as the write blocker can block any evidence alteration actions.



1) Which tool is used to ensure data integrity during the collection?
=> WRITE BLOCKER

2) What is the name of the document that has all the details of the collected digital evidence?
=> CHAIN OF CUSTODY



## Windows Forensics

- The most common types of evidence collected from crime scenes are desktop computers and laptops
- Windows is OS used most of the time

- As part of the data collection phase, forensic images of the Windows operating system are taken. These forensic images are bit-by-bit copies of the whole operating system. Two different categories of forensic images are taken from a Windows operating system :

    -  Disk image:
        - The disk image contains all the data present on the storage device of the system (HDD, SSD, etc.).
        - This data is non-volatile, meaning that the disk data would survive even after a restart of the operating system.
        - For example, all the files like media, documents, internet browsing history, and more.

    - Memory image:
        - The memory image contains the data inside the operating system’s RAM. This memory is volatile, meaning the data will get lost after the system is powered off or restarted. 
        - For example, to capture open files, running processes, current network connections, etc.
        - Memory image has to be captured first because any restart or shut down will delete all of em


- Now we do have tools for capturind DISK and MEMORY image, ie :
    
    - FTK Imager : 
        - It is used to take disk images
        - This tool can also analyze the contents of a disk image. 
        - It can be used for both acquisition and analysis purposes.

    - AUTOPSY :
        - image analysis, including keyword search, deleted file recovery, file metadata, extension mismatch detection, and many more

    
    - DUMPLT : 
        - DumpIt offers the utility of taking a memory image from a Windows operating system. 


    - Volatility :
        - Analyzing memory imageS
        - supports various operating systems, including Windows, Linux, macOS, and Android.



1) Which type of forensic image is taken to collect the volatile data from the operating system?
=> MEMORY IMAGE



## PRACTICAL 

- Everything we do on our digital devices, from smartphones to computers, leaves traces

### Our cat, Gado, has been kidnapped. The kidnapper has sent us a document with their requests in MS Word Document format. We have converted the document to PDF format and extracted the image from the MS Word file for your convenience.

- In terminal i navigated and found the file where i had .doc, .pdf, .jpeg

- now whemever u write a .txt file or doc  metadata is always stored in the system and metadatac means time, date ,owner, modifications made , all of these information are called metadata, so all this will be stored in the system.

- Now in order to view this info for .pdf files, we gotta write the followinig command : ` pdfinfo DOCUMENT.pdf `

- For receiving the information for the images, ie metadata of images : ` exiftool IMAGE.jpg `