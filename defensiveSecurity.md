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



