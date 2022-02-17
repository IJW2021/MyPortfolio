![Logo](Images/PCOM7E.png)
[1](/MyPortfolio/PCOM7E/Unit01.html) | [2](/MyPortfolio/PCOM7E/Unit02.html) | [3](/MyPortfolio/PCOM7E/Unit03.html) | [4](/MyPortfolio/PCOM7E/Unit04.html) | [5](/MyPortfolio/PCOM7E/Unit05.html) | [6](/MyPortfolio/PCOM7E/Unit06.html) | [7](/MyPortfolio/PCOM7E/Unit07.html) | [8](/MyPortfolio/PCOM7E/Unit08.html) | [9](/MyPortfolio/PCOM7E/Unit09.html) | [10](/MyPortfolio/PCOM7E/Unit10.html) | [11](/MyPortfolio/PCOM7E/Unit11.html) | [12](/MyPortfolio/PCOM7E/Unit12.html)
### Week Seven [week Hebdomada septem]
So this week was all about risk and planning to remove risk as much as possible for me this was a good week for me as alot of the material was covering the sorts of questions I deal with on a daily basis in my job as a Solutions Architect and also having a foundation award in ITIL and being through numerous reviews including modern service management this was also a module that first of all refreshed some of the knowledge I allready had but also enabled me to understand some of the reasons why we do things the way we do which I have not had the chance before.

During this week I also continued my work with pentesting tools looking at infomation leakage this was quite successful as by using tools built into the OS (wget , curl) I was able to expose a number of subdomains such as wpanel webmail webdisk that we can imvestigate as potential ingress points into the web system. 

**Scan Result**

The Command we used to extarct the information was 
```console
echo | openssl s_client -showcerts -servername daedalus-systems.tech-sourcery.co.uk -connect daedalus-systems.tech-sourcery.co.uk:443 2>/dev/null | openssl x509 -inform pem -noout -text | grep -e DNS
```

Which returned the following doamins that my team are going to investigate further

- DNS:daedalus-systems.co.uk
- DNS:autodiscover.daedalus-systems.co.uk
- DNS:cpanel.daedalus-systems.co.uk
- DNS:cpcalendars.daedalus-systems.co.uk
- DNS:cpcontacts.daedalus-systems.co.uk
- DNS:daedalus-systems.tech-sourcery.co.uk
- DNS:mail.daedalus-systems.co.uk
- DNS:webdisk.daedalus-systems.co.uk
- DNS:webmail.daedalus-systems.co.uk
- DNS:www.daedalus-systems.co.uk
- DNS:www.daedalus-systems.tech-sourcery.co.uk




**Weekly Skills Matrix New Knowledge Gained**

- [x] Security Tooling (Metasploit , Fuzzers , Nessus)
- [X] Tool Evaluation 

**Happiness Level**

😀😀😀😀
