![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Ten [Hebdomada Decem]

![Logo](Images/Stats.png)

The plan to take a step back from coding sort of worked as the amount of time coding was down from last weekleaading to a less stressed Ian and some serious progress has been made as a team we did our first end to end test and we succesfully got our dataproducer sending data to our Kafka cluster which we have now built we then created a Kafka connector container that picked up the data and successfully used our API to write the data into our MariaDB. On a personal note it was great to see that after weeks of design and coding that the solution was viaiable. We now need a big push to smooth out the rough edges and to start documentation on the infrastructure and coding side of the work.

We also got some key tecnology working we have now implemented watchtower on our web hosts (Docker) that when a new image is produced via our automated Github actions new docker containers get buildt on every push to the main branch it will see that and automatically update the running container with the new version without us having to manually reconfigure the hosts. 


**Weekly Skills Matrix New Knowledge Gained**

- [x] How To Build a Kafka 3 Node Cluster 
- [x] Firewall Configuration
- [x] Setup of Docker Watchtower 

**Happiness Level**
