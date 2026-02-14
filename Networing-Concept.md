# NETWORKING CONCEPTS
# -------------------

- Networking is nothing but how data packets are sent over the internet 

- There are 7 ayers in TCP/IP model
    - PHYSICAL
    - DATA LINK
    - TRANSPORT
    - SESSION
    - PIZZA
    - AWAY

- Ipv4 and ipv6 are 2 types

- ipv4 is 32 bits

- ipv6 is 128 bits
- Then we have 2^32 ipv4 addresses
- Tho we have 2^32 ip addresses, it wont be sufficient for us to distribute it to each and eveyr other devices, hence for this wehjave introduced PRIVATE NETWORK 
- NAT ( NETWORK ADDRESS TRANSLATOR) It assignes private ip address to devices and when deive wanna communicate with internet outside private address, then NAT send its to the internet 
- Subnetting is dividing the network so that we can spilt the local netowork and innsolate them from eachotehr

- TCP is connection oriented 

- UDP is connection less

- TCP -> Transmission control protocl [ 3way handshake ]
    - SYN
    - SYN ACK
    - ACK

- UDP-> user datagram protocol

1) On a WiFi, within what will an IP packet be encapsulated?
-> Frame


2) What do you call the UDP data unit that encapsulates the application data?
-> Datagram

3) What do you call the data unit that encapsulates the application data sent over TCP?
-> Segment

- TELNET -> TELETYPE NETWORK

- It runs on port 23 , and is used to connect to other remote deivces

- `tcp  macine_ip  port_number` is the command

- DHCP -> DYNAMIC HOST CONTROL PROTOCOL

- DHCP is an application-level protocol that relies on UDP; the server listens on UDP port 67, and the client sends from UDP port 68.

- Now whenever we connect to internet , ip address will be assigned to our device, which we can either do automatically or DHCP will do this assigning work for us

- DHCP Assigns ip address using DORA process 
    - It has 4 steps
        1) DHCP DISCOVER

        2) DHCP OFFER

        3) DHCP REQUEST

        4) DHCP ACKNOWLEDGE

- So the DORA is as follows , Initially device will have an ip address ->0.0.0.0 assigned and then it will broadcast its request if need for ip address to 255.255.255.255 and then DHCP will offer an ip address to the device and thgen device will requrest for this ip address and then DHCP will acknowledge the request and assign the ip address

- ARP -> ADDRESS RESOLUTION PROTOCOL

- If devices wanna communicate with other devices on the same network it must know the mac address of the other network
- MAC -> media access control
- MAC is 48 bit number

- So the process is as follows , device 1 wanna communicate with device 2 on the same netowrk but dont know where is dev2 , so the dev 1, broadcasts message using ff:ff:ff:ff:ff:ff:ff:ff , asking for dev2's ip address , this search / broadcast is done by ARP, and then dev2, sees that his ip is being asked and the dev2 resppns with its ip and mac address, hence creating a communcation link

- TTL -> TIME TO LIVE .
- TTL indicates the maximum number of routers a packet can travel through before it is dropped

- Ping is used to ask the other device is up or no

### ROUTING PROTOCOLS

1) OSPF -> Uses path cost and has table of info of all the paths across all routers , within network , fast [ Open shortest path first ]

2) EIGRP -> cisco based , combo of multiple protocols [Enhanced Interior Gateway Routing Protocol ]

3) BGP -> btw internet , [ BORDER GATEWAY PROTOCOL ]

4) RIP -> [Routing Information Protocol] hops , used in small network , max 15 hops


## NETWORKING CORE PROTOCOLS

- DNS -> DOMAN NAME SYSTEM
- Our browser doesn undertsand what is google.com or any website name we type , it knows only ip address, but humans cant remember ip address, this is where DNS came into use, so DNS has all the doman name and ip addresses assigned to each other , so when i types google.com , the ip address is found by DNS asnd thesefore i get the result . 

- DNS has a table with few record 
    - A Record -> maps domain name to ipv4
    - AAAA -> domain to ipv6
    - CNAME -> Canonical name , like www.example.com can be writtein as example.com , both are same
    - MX -> main exchanges it gives mail linked to the particular domain

- commmand to get ip address of domain -> `  nslookup www.example.com  ` 

## WHOIS

- ` whois domain_name.com ` This is command used to give information about the registered domain name

- we can hide our domain info from who is 

- To get hidden details We can use
    - whois [domainname].com    -----> for hidden [ this gives us info about domain we are searching for ]

    - whois domainname.com        -----> normal [ this gives us info about domain we are searching for ]

- HTTP Stand for hyper text transfer protocol

- HTTPS , same as HTTP , but s is secure

- GET  -> get info about / from server

- POST -> allows us to submit new data to the server, such as submitting a form or uploading a file.

- PUT -> is used to create a new resource on the server and to update and overwrite existing information.

- DELETE ->  is used to delete a specified file or resource on the server.

- HTTP uses port 80

- HTTPS uses port 443

- FTP, Stand for file transfer protocol , and is used for  transfer files. It  listen on port TCP 21
    - USER is used to input the username
    - PASS is used to enter the password
    - RETR (retrieve) is used to download a file from the FTP server to the client.
    - STOR (store) is used to upload a file from the client to the FTP server.

- ` ftp machine_ip `   [ helps us to connect to ftp port of the machine_ip ]

- SMTP -> SIMPLE MAIL TRANSFER PROTOCOL .This is used for email to talk to each other and to the mail server as well
    - HELO or EHLO initiates an SMTP session
    - MAIL FROM specifies the sender’s email address
    - RCPT TO specifies the recipient’s email address
    - DATA indicates that the client will begin sending the content of the email message
    - `.` is sent on a line by itself to indicate the end of the email message


- The SMTP server listens on TCP port 25 by default.


# TCP DUMP --> PACKET CAPTURE

- TCP dump is used to capture the packets and then we can analyze these captured packets via WIRESHARK

- `tcpdump -i INTERFACE` --> Captures packets on a specific network interface
- `tcpdump -w FILE` -->	Writes captured packets to a file
- `tcpdump -r FILE`	--> Reads captured packets from a file
- `tcpdump -c COUNT` --> Captures a specific number of packets
- `tcpdump -n`	--> Don’t resolve IP addresses [ resolve in the sense, converting ip_addresse to respsective domain names]
- `tcpdump -nn`	--> Don’t resolve IP addresses and don’t resolve protocol numbers [ resolve protocol mean, conver port number to their port_name]
- `tcpdump -v`	--> Verbose display; verbosity can be increased with -vv and -vvv

- `tcpdump -i eth0 -c 50 -v` -->  captures and displays 50 packets by listening on the eth0 interface, which is a wired Ethernet, and displays them verbosely.

- `tcpdump -i wlo1 -w data.pcap` -->  captures packets by listening on the wlo1 interface (the WiFi interface) and writes the packets to data.pcap. It will continue till the user interrupts the capture by pressing CTRL-C.

- `tcpdump -i any -nn`--> captures packets on all interfaces and displays them on screen without domain name or protocol resolution.


- `tcpdump host IP` or `tcpdump host HOSTNAME`	--> Filters packets by IP address or hostname
- `tcpdump src host IP` -->	Filters packets by a specific source host
- `tcpdump dst host IP` -->	Filters packets by a specific destination host
- `tcpdump port PORT_NUMBER` --> Filters packets by port number
- `tcpdump src port PORT_NUMBER`--> Filters packets by the specified source port number
- `tcpdump dst port PORT_NUMBER` --> Filters packets by the specified destination port number
- `tcpdump PROTOCOL` --> Filters packets by protocol; examples include ip, ip6, and icmp


- `and`: Captures packets where both conditions are true. For example, tcpdump host 1.1.1.1 and tcp captures tcp traffic with host 1.1.1.1.

- `or`: Captures packets when either one of the conditions is true. For instance, tcpdump udp or icmp captures UDP or ICMP traffic.

- `not`: Captures packets when the condition is not true. For example, tcpdump not tcp captures all packets except TCP segments; we expect to find UDP, ICMP, and ARP packets among the results.

- `greater LENGTH`: Filters packets that have a length greater than or equal to the specified length
- `less LENGTH`: Filters packets that have a length less than or equal to the specified length

- binary operations:` &, |, and !` --> nothing but 0 & 1 --> 0 [ simillarly for all]

- `tcpdump "tcp[tcpflags] == tcp-syn"` to capture TCP packets with only the SYN (Synchronize) flag set, while all the other flags are unset.
- `tcpdump "tcp[tcpflags] & tcp-syn != 0"` to capture TCP packets with at least the SYN (Synchronize) flag set.
- `tcpdump "tcp[tcpflags] & (tcp-syn|tcp-ack) != 0"` to capture TCP packets with at least the SYN (Synchronize) or ACK (Acknowledge) flags set.0

## DISPLAYING TCP DUMP PACKETS

- `tcpdump -q`	Quick and quite: brief packet information
- `tcpdump -e`	Include MAC addresses
- `tcpdump -A`	Print packets as ASCII encoding
- `tcpdump -xx`	Display packets in hexadecimal format
- `tcpdump -X`	Show packets in both hexadecimal and ASCII formats