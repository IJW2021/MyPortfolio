![Logo](Images/Logo.png)
[1](/MyPortfolio/SEPM/Unit01.html) | [2](/MyPortfolio/SEPM/Unit02.html) | [3](/MyPortfolio/SEPM/Unit03.html) | [4](/MyPortfolio/SEPM/Unit04.html) | [5](/MyPortfolio/SEPM/Unit05.html) | [6](/MyPortfolio/SEPM/Unit06.html) | [7](/MyPortfolio/SEPM/Unit07.html) | [8](/MyPortfolio/SEPM/Unit08.html) | [9](/MyPortfolio/SEPM/Unit09.html) | [10](/MyPortfolio/SEPM/Unit10.html) | [11](/MyPortfolio/SEPM/Unit11.html) | [12](/MyPortfolio/SEPM/Unit12.html)

![Logo](Images/Diary.png)
### Week Eight [Hebdomada Octo]

So we have reached week eight already scary how fast the module is progressing this week has been a week of looking at data structures in Python an Interesting topic and one that will be useful outside of just the SEPM module and those bits of content and knowledge tend at least in my opinion are the bits of content I enjoy learning as they can be applied to new situations and make me a better developer / IT Subject Matter Expert.

## Excerise

**Data Structures**

The Data Structures we want to use to hold the functional and non-functional requirements need to first to be able to hold text but we also need to hold a secondary information on if the stored data is a functional requirement.

**List** 

The List while allowing us to store requirement does not allow for the separation of functional and non-functional requirements

| requirements  | requirements  | requirements  | requirements  | requirements  |
|---|---|---|---|---|


We can however expand the use of lists by combining with another data structure such as a tuple to hold the type along with the requirement in a list

**List of Tuples**

| (Type, requirements)  | (Type, requirements)  | (Type, requirements)  | (Type, requirements)  | (Type, requirements)  |
|---|---|---|---|---|

This allows the type and the requirement to be stored along with the actual requirement.

This would work but would require us to process the entries to identify which are functional or non-functional devices a better solution is to use a dictionary

**Dictionary of Lists**

| Functional  | [LIST]  |
|---|---|
| Non Functional   | [LIST]  |

**Pure Dictionary**

| F1  | ITEM  |
|---|---|
| F2  | ITEM  |
| NF1  |ITEM  |
| NF2  |ITEM   |

A list can store a series of items in a certain order meaning you can index into the list, or iterate over the list. A dictionary on the other hand is an example of a hash table structure and is a key-value type of structure. it requires that the dictionary keys are hash table. The advantage of this structure is speed of lookups

On The Project side Weekly meeting was positive and I think we have an initial direction we want to take I have taken it upon myself to get the infrastructure side setup so that we have a platform we can host the application on its all going to be based on Microservices so planning on going with a standard Linux Host running the docker engine but will confirm with the team developers if they need anything outside of that.

**To DO My Actions for the next week**

- Setup Linux Host
- Install Docker Engine
- Install Portainer To Manage Docker Engine
- Install Webmin to Manage Host
- Ensure all updates have been applied 
- Setup a Domain Name for Project
- Move DNS to CloudFlare
- Decider on Hosting Provider (Azure , AWS , GCP , SelfHosted)


This has been a good week we have a direction just need to steer the course and deliver on the potential the test will be the delivery but so far looking good and feeling positive time will tell if that is well founded.

**Weekly Skills Matrix New Knowledge Gained**

- [x] Refresher on Python DataTypes
- [x] Infrastructure Build Out

**Happiness Level**
😀😀😀😀😀
