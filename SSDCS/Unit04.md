![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)

### Week Four [Hebdomada quattuor]
A new week and after some critical thought a few changed to the infastructure design I have been working on for our project solution with one of the key goals we have set ourselves as a team is to make ours a HA highly avaiable solution in that end one of the weak points was our ingress point to the solution as any failure there would have prevented access to our API and services. to overcome this I have added two new servers at the perimeter of our solultion these are both configured with the HAproxy software in loadbalancing mode so if any one of our backend servers goes offline requests will get redirected to one of the servers that are still avaiable. The proxy servers themselves are configured as a pair a primany node and a failover node so if the main proxy server goes off line the secondary server takes over this was done by the use of VIPs (Virtual IP Address) as this means we can have one address that floats between the two VMs. HA is changelling as you have to look at every step of your design and ask the question how would the system work if the component or service failed but it is quite rewarding coming up with solutions.

**Meeting**

Good meeting to dicuss project work got notification that from an initial team of 4 we are now a team of 3 or 2+1 when you take into account time difference isues got to admit silghtly concerned that due to the reduced numbers we are now going to be at a disadvantage when compared to the other teams but to parapharase the British Armed forces adapt and oversome so that is what we will do.but in sightly better news we are cracking on with our design document 📄 and are looking to use some quite interesting technology as part of that and our Drive for HA we have put using a active directory domain into our design as this will aid security and airgaps the web interface and user account info as we will only be sending NTLM hashes over the network to test this I also redid my LDAP proof of concept using the ldap3 python library as this has more options then the ldap Library we were going to use and please to say it works 

```python
from ldap3 import Server, Connection, ALL, NTLM
from ldap3.core.exceptions import LDAPInvalidCredentialsResult

try:
    s = Server('192.168.0.200', port=389, get_info=ALL)
    c = Connection(s, user="ssdgroup3\\Administrator", password='Rosedale02$', check_names=True, lazy=False, raise_exceptions=True, authentication=NTLM)
    c.open()
    c.bind()
    c.search('OU=Users,OU=Nasa,DC=ssdgroup3,DC=info', search_filter='(&(userPrincipalName=Ian.Wolloff@ssdgroup3.info)(objectclass=user))')

    print('Hello ', str(c.entries).replace('[DN: CN=', '').split(',')[0], 'Logged in on DOMAIN ', [x1.upper() for x1 in str(c.entries).replace('[DN: CN=', '').split(',') if 'DC' in x1][0][3:])
except LDAPInvalidCredentialsResult:
    print("Wrong Password")
    
```

**Slack Post about what language is better for a OS**
Interesting question but a bit misleading as when we think of an operating system we think of a desktop PC or mobile device in this sense python would be a bad choice if not impossible due to python being a high level interpreted language  it would not have the low level access to carry out standard OS 
functions

* File Management
* Network Management
* Memory Management
* Secondary Storage Management (HDD,SSD,NVME)
* I/O Management
* Security Management
* Command Interpreter System

That being said if we consider a device such as a embedded controller such as a pi pico this can run a stripped down version of python :snake:  (MicroPython) that has enough low level control to be considered a OS but C would still be the better choice as while having a far larger learning curve and being harder to do well for a OS you need the low level access to the hardware and compiled languages such as C give this along with better performance which in a real time applications such as a OS is an important consideration. Part of good system design is also using the right tools for the right situations and in this case you would use C rather than python as it gives you more options or as said by Linus Torvalds. "Nothing is better than C programming language" https://www.youtube.com/watch?v=CYvJPra7Ebk

## Thread Exercise ##

Carried out the python exercise

```Python
code source: https://techmonger.github.io/55/producer-consumer-python/
 
from threading import Thread
from queue import Queue
 
q = Queue()
final_results = []
 
def producer():
    for i in range(100):
        q.put(i)
        
 
def consumer():
    while True:
        number = q.get()
        result = (number, number**2)
        final_results.append(result)
        q.task_done()
   
   
for i in range(5):
    t = Thread(target=consumer)
    t.daemon = True
    t.start()
    
producer()
 
q.join()
 
print (final_results)
```

**How is the queue data structure used to achieve the purpose of the code? **

The Queue structure is acting as a stack FIFO taking the output of the threads and storing the results into a single structure 

**What is the purpose of q.put(I)?**

This statment takes the current value of the loop itterator (I) and places the value into the queue structure q i.e the value is pushed into the queue if for example the current queue held the value shown below

| 1  | 3 | 4  | 2  |
|---|---|---|---|

and the value of I was 5 the queue would become

| 1  | 3 | 4  | 2  | 5 |
|---|---|---|---|--|


What is achieved by q.get()?
What functionality is provided by q.join()?
Extend this producer-consumer code to make the producer-consumer scenario available in a secure way. What technique(s) would be appropriate to apply?



Intersting excerise and shows the issues of predicting sequence and concurency when dealing with independent threads.

**Regex**

Also wrote some code lookign at validation of Postcodes using regex very close to my actual day job this one as its something i have written numerous times over the years as part of data migration projects and FOI requests but never in python 🐍 as I usualy write the regex at the DMBS level using Oralce regex operators so it was nice to see how python does it. And just because it was interesting wrote some code to call a public API to validate postcodes using the public API hosted at https://api.postcodes.io 

```python
from typing import Dict, List

# Postcodes to test With
POSTCODE = ['M1 1AA', 'M60 1NW', 'CR2 6XH', 'DN55 1PT', 'W1A 1HQ', 'EC1A 1BB']


# Regex Tests
def validate_pcode(pcode: List[str]) -> Dict[str, bool]:
    RESULT = {}
    for x in pcode:
        if any(re.findall(r'\b[A-Z]{1,2}[0-9][A-Z0-9]? [0-9][ABD-HJLNP-UW-Z]{2}\b', x)):
            RESULT[x] = True
        else:
            RESULT[x] = False
    return RESULT


# Lookup Postcodes using Public API
def api_validate(pcode):
    result = {}
    headers = {'Content-type': 'application/json', 'Accept': 'text/plain'}
    api = requests.post(url='https://api.postcodes.io/postcodes/', json={"postcodes": POSTCODE}, headers=headers)

    for x in api.json()["result"]:
        if x['result'] is not None:
            result[x["result"]["postcode"]] = True
    return result


print(validate_pcode(POSTCODE))
print(api_validate(POSTCODE))
```

Busy week and still not a fan on RegEx expressions though will admit they are quite useful just a bit of a pain to put together had some good meetings with some good ideas. 

**Weekly Skills Matrix New Knowledge Gained**

- [x] Threading
- [x] RegEXs

**Happiness Level**

😀😀😀
