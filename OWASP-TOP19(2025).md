# ROOM NAME :  IAAA Failures

## The mission

- In this room, i learnt about IAAA and how weakness here can cause issues 

- IAAA -> INTEGRITY , AUTHENTICATION , AUTHORIZATION AND ACCOUNTABILITY

## Progress

- A01 -> BROKEN ACCESS CONTROL ( IDOR) -> its like changing the ID in the URL section of the website and gaiining access to others account
    - example : https://bank.thm/accounts?id=5 (changing id)



- A07 -> Authentication Failures -> So , as we know , we need usrname and pass, for logging in . Now , in some cases, the backend normalized (ie ignores the case ) , this leads ti authentication failure. Example : admin : qqqqq ( admin's credential) , now the backend has A07, So hacker registers with a new id such as -> aDmiN:123 -> and then when the hacker tries to log in as aDmiN:123 , because of case sensitivity ignored by backend , what happens is , the hacker gets access to the admin account .


- A09: Logging & Alerting Failures -> Its very important to keep logs on what user is doing, else if anything goes wrong, its very difficult to figutre out what happened , when , why and how 


## Tools and commands used 

- Nothing used .

## Mistakes to avoid .

- A01 => Never trust the frontend. Always check permissions on the server.

- A07 => Never confuse identities. Always know exactly who logged in.

- A09 => If something bad happens, you must see it in logs.







# OWASP Top 10 2025: Application Design Flaws


## THE MISSION 

- AS02: Security Misconfigurations
- AS03: Software Supply Chain Failures
- AS04: Cryptographic Failures
- AS06: Insecure Design


## PROGRESS

### AS02: -> SECURITY MISCONFIGURATIONS

- This is not a flaw in the code, rather this happens because of logic error or human errors

- Taking examples , i would say , like leaving unnecessary endpoints open, verbose logic errors ( this is like , when an error pops up in the website, instead of saying " Not found "  it give us the information regardiing the website as well ), weak credential ( default creds left unchanged ) .

- Here , i just went to the mentioned website -> then i saw , it had endpoiints such as api/user/123 -> so in the url section i type the same and then i found there was a user names John Dor and then in place of 123 , i wrote John Doe and hence got the flag




### AS03: Software Supply Chain Failures

- Sometimes while creatiing code, we directly use dependencies / import packages from outside and when these iimported packages have flaw, and we use it , it jhappnes to create a hole in out entire system itseelf.

- For this task , all i did was went to the website , k and then i found , two methods were beig shown -> POST(api/process) and GET(api/health)  -> i tried the get in url , and it showed me the status -> now for post, i neede to use json application and needed to input data, so i cant directly do this in URL , so i used ` curl -X http://url/api/process -H content-type:"applicatio/json" -d '{"data":"debug"}'` for POST method and got the flag



### AS04: Cryptographic Failures

- This happens when u use weal algoritms/ pass

- Here task was simple , when i went to website , i found a encrypted document and had to decrypt it . I inspected the page first -> then i went to html code and in there i fouund a code "src = static/js/decrypt.js" , so i typed the same in url and then i gopt the key , and used online decrypted to decryt the document




### AS06: Insecure Design

- This was also same , dont use weak pass and human errors

- Easy tak , went to url , and then did /api/users -> got few users adn then did -? url/api/users/admin -> got admin details and then tried this -> url/api/messages/admin -> yeah , this gave me the flag


## COMMAND USED

` curl -X http://url/api/process -H content-type:"applicatio/json" -d '{"data":"DATA"}'`


#
# OWASP Top 10 2025: Insecure Data Handling


## MISSION

- A04: Cryptographic Failures
- A05: Injection
- A08: Software or Data Integrity Failures


## PROGRESS

- Cryptographic failure is same as using weak algo , weak passwords, unverified TLS

- Injection is like adding weird command / linux command into forms present in website

- software or data integrity failure , this happens when u use third party dependencices or updates the app without knowing about it 