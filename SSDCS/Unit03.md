![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Three [Tres Sabbati]

Started to think about the project and in particular authentication of client so built a domain controller vm to try out some ideas 

![Logo](Images/ESXI.png)

with this I manged to write a python script that would authenticate against the windows active directory. One that may take forward into our team project

```python
# Authenticate Against a Windows Active Directory Domain Controller
# https://www.python-ldap.org/en/python-ldap-3.4.0/
import ldap

try:
    ldap.set_option(ldap.OPT_REFERRALS, 0)
    ldap.protocol_version = 3
    conn = ldap.initialize('ldap://192.168.0.111')
    conn.simple_bind_s('CN=Administrator,CN=Users,DC=ad,DC=ssdgroup3,DC=info', 'letmein')
    print("Hello", str(conn.whoami_s()).split('\\')[1])
    print("Auth OK")
    conn.unbind()
except ldap.INVALID_CREDENTIALS:
    print("Auth Failure")

```

**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
