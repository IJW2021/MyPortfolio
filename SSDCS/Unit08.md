![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Eight [Hebdomada Octo]

Positive but also slightly anoying start to the week on the postive side infrastructure build out is on schedule even with our change to base os which is turning out to be a good decision as a our VM images have reduced in size from 150GB per VM down to about 9GB per image while storage is not a big concern our current storage array has a 8TB ZFS pool smaller is better on a secuirty side as it means the attack surface of the OS underpinning our service is reduced. 

**DR and BCP**

Along with the actual delivery we need to think about our Disaster recovery position as a solutuon needs to be able to recover from unforseen events and as our domain is in a hostile environment this is important. To this regard as part of our plan is to include backup and recovery solution as the industry leader and because there is a free tier we have gone with a VEEAM based solution.

![Backup](Images/backup.png)

Been a good week on the project gone from a idea to a proposal and now to the start of a actual product there are three main parts of our solution

* User Interface
* Data Collection
* APIs

I have been asigned the task of buildig the APIS that the rest of the solution will use while not the part of the project that has the wow factor without a strong underpinning the services that are built on top of the APIS will suffer so have been reading up on API Design the Flask Micro framework and JWT tokens. As I want to build a strong set of APIs 

We had a good dicussion about encryption which was quite interesting so wrote a quick ROT13 which I class more of a encoding techninque then a real encryption standard actually rember using it when talking part in usenet dicussion forums back in the eary 90s

```python
def rot13(q: str) -> str:
    result: list = []
    for x in q:
        if x.isalpha():
            shift = 13 if 'Z' < x < 'n' or x < 'N' else -13
            result.append(chr(ord(x) + shift))
        else:
            result.append(x)
    return ''.join(result)
```

**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
