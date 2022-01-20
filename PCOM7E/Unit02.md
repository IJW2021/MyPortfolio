![Logo](Images/PCOM7E.png)
[1](/MyPortfolio/PCOM7E/Unit01.html) | [2](/MyPortfolio/PCOM7E/Unit02.html) | [3](/MyPortfolio/PCOM7E/Unit03.html) | [4](/MyPortfolio/PCOM7E/Unit04.html) | [5](/MyPortfolio/PCOM7E/Unit05.html) | [6](/MyPortfolio/PCOM7E/Unit06.html) | [7](/MyPortfolio/PCOM7E/Unit07.html) | [8](/MyPortfolio/PCOM7E/Unit08.html) | [9](/MyPortfolio/PCOM7E/Unit09.html) | [10](/MyPortfolio/PCOM7E/Unit10.html) | [11](/MyPortfolio/PCOM7E/Unit11.html) | [12](/MyPortfolio/PCOM7E/Unit12.html)
### Week Two [week Duo]
As this was the first time I had done IT security this week was spent doing quite a bit of backgound reading around the topic along with building a pentest PC that I could user for the upcoming project work. Looking forward to picking up some new skills in the area of IT and application security.

### Forum Post ###
The healthcare arena is an area where traditionally the security of devices and services is often not the primary concern security often came as an afterthought when designing and implementing medical network enabled devices. This approach however no longer works in a modern world with IOT connected devices, combined with big data and cloud services. While Security is only one aspect of a system / application it is a vitally important part. But once a system is a connected system then as security researcher Dan farmer said

 “If security were all that mattered, computers would never be turned on, let alone hooked into a network with literally millions of potential intruders”

― Dan Farmer (Anon)

In the study “Compromising a Medical Mannequin” the idea that was examined was whether an individual or entity could breach / bypass the security systems of a medical training mannequin. The answer to that question from the research that took place was a yes. though this research two types of attack vectors were identified the first was a denial of device attack (DOS) on the medical device this type of attack is designed to limit the availability of service by flooding the service with requests to an extent that the service is unable to process all the requests being received.

Mitigation against these DOS attacks can be difficult but tend come into categories of traffic analysis to ensure that an excessive demand on the service or services is not coming from a single address or from known bad actors. This in turn has led to the attackers deploying a variation of the DOS attack the DDOS (Distributed Denial of service) attack where the DOS traffic is distributed across a number of nodes most often in separate geographical locations and law enforcement boundaries. Mitigation against DDOS attacks is harder but can be achieved by the use of traffic inspection, firewall rules and putting the service behind firewalls (Network Layer and Application) along with shielding services behind content delivery services designed to detect and defend against these types of attack.

The Second type of attack that was employed was a brute force attack on the WIFI (Anon) this type of attack tries to guess all possible combinations of username, password or pin until a correct value is found. While this can be effective attack against shorter data or data of a known length today this is mostly not an affective attack today as it can be easily mitigated against by

1.    Forcing Complex passwords (Mix of Upper Case , Lower Case , Numbers and special characters)

2.    Locking accounts after x number of wrong guesses

3.    Implementing a Two Factor (2FA) authentication strategy (Anon)

4.    Ensuring any password hashes are salted to prevent pre-computation attacks (Rainbow Tables)

5.    use of Biometrics (Fingerprints, Face Detection etc)

Employing these measures along with some form of heuristic based IDS solution and having a proper triple AAA (Access Control, Authentication, Auditing) approach to security helps to minimises the attack vector any attacker would have.

The outcome of these tests shows that proper security is hard and needs to be built into the design of hardware, software and systems from the design through to production this can also be seen by the devastating impact lack of security can have in healthcare where a security vulnerability can indeed cost lives. there is a good paper on this subject “Healthcare Data Breaches: Insights and Implications” (Seh et al., 2020)

References 

 Seh, A. H. et al. (2020). Healthcare Data Breaches: Insights and Implications. Healthcare, 8 (2). [Online]. Available at: doi:10.3390/HEALTHCARE8020133 [Accessed 14 November 2021].

“Krack” Wi-Fi guidance - NCSC.GOV.UK. [Online]. Available at: https://www.ncsc.gov.uk/guidance/krack [Accessed 14 November 2021a].

Multi-factor authentication - Wikipedia. [Online]. Available at: https://en.wikipedia.org/wiki/Multi-factor_authentication [Accessed 14 November 2021b].

Security Quotes. [Online]. Available at: https://www.nativeintelligence.com/resources/security-quotes/ [Accessed 14 November 2021c].

**Weekly Skills Matrix New Knowledge Gained**

- [x] Different Types of Security Issues
- [X] Greater understanding that security can be hard

**Happiness Level**

😀😀😀😀
