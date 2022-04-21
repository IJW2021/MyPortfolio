![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Seven [Hebdomada Septem]

So our team proposal has finally been submitted 🥳 but we had to be brutal with the editing to get the submission within the word limit for the next set of students who do this module please raise the word limit as we had to cut quite a few well researched sections just to get it in under a imposed limit. that being said quite happy with our proposal but now we have to implement what we have designed 

In other project news backend infrastructure build out has had both a good and negitive week on the good side we have now got DR and a backup solution in place so in the event of any issues we can recover our indvidual components on the not so good side a new version of the core Linux Distro we plan to use is due to be released this week so I may need to rebuild some of our platform to take advantage of the improved secrity included in the new version if nothing else it has a cool name **22.04 Jammy Jellyfish** I thought that now the final proposal has been submitted in these weekly posts I wold include some information on the build process and what has changed from our initial plan as "no plan lasts past first contact with the enemy" [Field Marshal Helmuth von Moltke] so I 100% expect that there will need to be changes to the design in the delivery phase of the project.

**Weekly Change to Proposal**

| Area  | Change  |
|---|---|
| OS  | Update to Linux 22.04  |
| Container  | Inclusion of WatchTower container to autoupgrade containers |
| Storage | Moved Local Storage to ZFS ISCII Block Storage |


New Patch released for Vmware ESXI so patched our Vmware host to the latest7.0U3D version to get the latest hotfixes

```shell
esxcli network firewall ruleset set -e true -r httpClient
esxcli software profile update -p ESXi-7.0U3d-19482537-standard -d \
https://hostupdate.vmware.com/software/VUM/PRODUCTION/main/vmw-depot-index.xml
esxcli network firewall ruleset set -e false -r httpClient
```

**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
