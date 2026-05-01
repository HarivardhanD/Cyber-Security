DONE ANKI

# EDR --> ENDPOINT DETECTION AND RESPONSE

- `Endpoint Detection and Response (EDR)` is a security solution designed to monitor, detect, and respond to advanced threats at the endpoint level. 


- `EDR` is used for host level detection [ FOR SPECIFIC EDNPOINT ] and not `NETWORK` level detection
- Here endpoints are not URL but physical devices used by the Employees :
    - laptops
    - server
    - mobile devices

- 3 PILLARS OF EDR SOLUTION :
    - `VISIBILITY`
        - COLLECTS DETAILS DATA FROM ENDPOINTS
        - SUCH AS : PROCESS MODIFICATIONS , REGISTRY MODIFICATIONS, FILE AND FOLDER MODIFICATIONS, USER ACTIONS ETC
    - `DETECTION`
        - It has `behaviour` and `signature` based detections
    - `RESPONSE`
        - All this detectiona and visibilty is availbale for analyst at `CENTRAL EDR` .
        - Hence analyst can take perform actions on it based on threat detected .


- WHY `EDR` when we have `ANTI VIRUS` on endpoints ?
    - The `Antivirus (AV)` may detect some basic threats, but to detect advanced threats that evade normal detections, we need an EDR


- AN EDR works as follows :
    - Every endpoint has a `AGENT` or `SENSOR` which collects dats continuosouly and performs real time threat detection and blocking
    - Then this logs are sent to the `EDR CONSOLE` where deeper analysis and threat detections are done based on the behavioural analysis
    - Based on the alert and prioritization , Analyst take req actions


- EDR AGENTS --> COLLECTS DATA AND PUSH TO EDR CONSOLE --> THIS DATA IS CALLED `TELEMETRY`

-  EDR collects detailed telemetry from the endpoints. 


- `CONFIGURATION Setting` of windows are primarily stored on `REGISTRY`


- Based on `TELEMETRY` received from endpoints , DETECTIONS INCLUDE :   
    - BEHAVIORAL DETECTION
    - ANOMALY DETECTION
    - IOC MATCHING ( IOC = INDICATOR OF COMPROMISE ) --> Compares telemetry against threat intelligence feeds
    - MITRE ATT&CK MAPPING
    - MACHINE LEARNING ALGORITHM

- WHAT TO DO AFTER DETECTION OF MALICIOUS ACTIVITY?
    - ISOLATE HOST
    - TERMINATE THE PROCESS RESPONSIBLE FOR THE ACTIVITY
    - QUARANTINE THE MALICIOUS FILE
    - REMOTE ACCESS --> ANALYST TAKE CONTROL OF ENDPOINT AND PREVENT THE ATTACK