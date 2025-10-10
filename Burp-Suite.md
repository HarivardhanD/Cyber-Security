# INTRODUCTION

- Burp Suite is a Java-based framework designed to serve as a comprehensive solution for conducting web application penetration testing.

- Burp Suite captures and enables manipulation of all the HTTP/HTTPS traffic between a browser and a web server. 

- The ability to intercept, view, and modify web requests before they reach the target server or even manipulate responses before they are received by our browser makes Burp Suite an invaluable tool for manual web application testing.

- Burp suite professional -> This is the best version which has almost all the features used for web application pentesting and also used by professionals.

- Burp suite Enterprise -> This ones advantage is , it is used for scanning, yes its major power is scannig.

- We will be using  burp community additon, which tho does not have all the features, but is good for beginners and free of cost.

- Important key words, when using BURP :
    - Proxy: The Burp Proxy is the most renowned aspect of Burp Suite. It enables interception and modification of requests and responses while interacting with web applications.

    - Repeater: Another well-known feature. Repeater allows for capturing, modifying, and resending the same request multiple times.

    - Intruder: Despite rate limitations in Burp Suite Community, Intruder allows for spraying endpoints with requests. It is commonly utilized for brute-force attacks or fuzzing endpoints.

    - Decoder: Decoder offers a valuable service for data transformation. It can decode captured information or encode payloads before sending them to the target.

    - Comparer: As the name suggests, Comparer enables the comparison of two pieces of data at either the word or byte level. 

    - Sequencer: Sequencer is typically employed when assessing the randomness of tokens, such as session cookie values or other supposedly randomly generated data. 

    - Tasks: The Tasks menu allows you to define background tasks that Burp Suite will perform while you use the application.

    - Event log: The Event log provides information about the actions performed by Burp Suite, such as starting the proxy, as well as details about connections made through Burp.

    - Issue Activity: This section is specific to Burp Suite Professional. It displays the vulnerabilities identified by the automated scanner, ranked by severity and filterable based on the certainty of the vulnerability.

    - Advisory: The Advisory section provides more detailed information about the identified vulnerabilities, including references and suggested remediations. 