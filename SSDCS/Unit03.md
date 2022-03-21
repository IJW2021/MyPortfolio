![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Three [Tres Sabbati]

This week I Started to think about the project and in particular authentication of clients so built a domain controller vm to try out some ideas 

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

![Logo](Images/LDAP.png)

Also as we plan to use multiple servers in our final project wrote some code to check if a server is up or down to enable smart routing of requests only to servers that are currently responding.

```python
def get_server_status(servers: list) -> list:
    servers_status = {}

    for x in servers:
        # Get Platform as Ping command syntax differs between windows and Unix/OSX
        if platform == "Windows":
            if os.system(f"ping {x} -n 1") == 0:
                servers_status[x] = 'OK'
            else:
                servers_status[x] = 'BAD'
        else:
            if os.system(f'ping -c 1 {x} > /dev/null 2>&1') == 0:
                servers_status[x] = 'OK'
            else:
                servers_status[x] = 'BAD'

    good_servers = [x for x, y in servers_status.items() if y == 'OK']
    bad_servers = [x for x, y in servers_status.items() if y == 'BAD']

    return [good_servers, bad_servers]


# Example of Use
Server_Status = get_server_status(['192.168.0.111', '192.168.0.14', '123.123.123.123'])
```
## Forum Response
In a traditional mainstream SSRF attack as in your example the hacker would trigger the remote server to make a connection to internal services within the perimeter of the infrastructure of the host. Or they would try to force the server to connect to external systems in order to leak sensitive data such as authorization tokens, usernames, passwords etc

One of the more interesting ways a SSRF can be leveraged it to use a SSRF weakness to attack the server itself that is hosting the application this involves forcing the application to make a request back to itself via the loopback network address (127.0.0.1 or localhost) as these addresses and hostnames would resolve back to the local device. 
An example of how this exploit cloud work is an application may query locally hosted REST API endpoints via a HTTP request. The attacker could try to visit the API endpoints directly. But these may be secured behind application firewalls and Access control Lists (ACLs) preventing accesses from external addresses.

If the request came from the local machine the access controls and firewall rules would be bypassed as the request would appear to come from a trusted internal host
References

Hacker-One Reports https://github.com/reddelexc/hackerone-reports/blob/master/tops_by_bug_type/TOPSSRF.md [Accessed 21.03.2022]
Calzavara Stefano (https://secgroup.dais.unive.it/wp-content/uploads/2020/03/more_server.pdf)
OWSAP https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html [Accessed 21.03.2022]

Good Evening of work as have managed to set the first component of what will be come our final solution 9 VMs to act as a HA cluster

* 3x Manager Nodes
* 3x Worker Nodes

All running Docker Swarm technology and setup to be HA and to also load balance

Along with that also setup a reverse SSL proxy so any connections to our services will be secured with Lets Encrypt SSL Certificates

![Logo](Images/Proxy.png)


**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
