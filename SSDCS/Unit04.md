![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Four [Hebdomada quattuor]
A new week and after some critical thought a few changed to the infastructure design I have been working on for our project solution with one of the key goals we have set ourselves as a team is to make ours a HA highly avaiable solution in that end one of the weak points was our ingress point to the solution as any failure there would have prevented access to our API and services. to overcome this I have added two new servers at the perimeter of our solultion these are both configured with the HAproxy software in loadbalancing mode so if any one of our backend servers goes offline requests will get redirected to one of the servers that are still avaiable. The proxy servers themselves are configured as a pair a primany node and a failover node so if the main proxy server goes off line the secondary server takes over this was done by the use of VIPs (Virtual IP Address) as this means we can have one address that floats between the two VMs. HA is changelling as you have to look at every step of your design and ask the question how would the system work if the component or service failed but it is quite rewarding coming up with solutions.

**Meeting**

Good meeting to dicuss project work got notification that from an initial team of 4 we are now a team of 3 or 2+1 when you take into account time difference isues but we are cracking on with our design document 📄 and are looking to use some quite interesting technology as part of that and our Drive for HA we have put using a active directory domain into our design as this will aid security and airgaps the web interface and user account info as we will only be sending NTLM hashes over the network to test this I redid my LDAP app using the ldap3 python library as this has more options then the ldap Library we were going to use and please to say it works 

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


**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
