![Logo](Images/Logo.png)
[1](/MyPortfolio/SEPM/Unit01.html) | [2](/MyPortfolio/SEPM/Unit02.html) | [3](/MyPortfolio/SEPM/Unit03.html) | [4](/MyPortfolio/SEPM/Unit04.html) | [5](/MyPortfolio/SEPM/Unit05.html) | [6](/MyPortfolio/SEPM/Unit06.html) | [7](/MyPortfolio/SEPM/Unit07.html) | [8](/MyPortfolio/SEPM/Unit08.html) | [9](/MyPortfolio/SEPM/Unit09.html) | [10](/MyPortfolio/SEPM/Unit10.html) | [11](/MyPortfolio/SEPM/Unit11.html) | [12](/MyPortfolio/SEPM/Unit12.html)

![Logo](Images/Diary.png)
### Week Nine [Hebdomada Novem]

All our project infrastructure is now in place 🥳 went with a 2x dual Xeon Servers with 256GB memory as it looks like the project will be more memory limited then processor limited Have installed by usual Linux Suite

- WebMin (To Allow the server to be remote managed)
- Docker (Container Engine)
- CertBot (To Allow generation of SSL Certs)
- Portainer Agent (To Allow Management in Portainer) 

The The Topic for this week was code quality this is a really intresting topic and we could proberly do a whole module on just this topic being able to take some code and then to refactor it to run better and be more effcient or easier to read and maintain is something as a developer I always try to do

### Code

One Example of this that I have used is the use in the past is the use of the MAP and lambda functions as this is a more effienct way of applying a function call to an itteritable the downside is for deveopers without experence of what these functions do it does make the code harder to understand and whenever you apply code quality changes you always have to access the value of the code quality chnage vs readbility and understandability of the code and make a judgement call on if the change is worth any reduction in the ability for the code to be understood.

```python
if all(list(map(lambda x: os.path.exists(x), ['space.ssdgroup3.info.pem', 'space.ssdgroup3.info.key', 'RootCA.pem']))):
    if all(list(map(lambda x: (generate_calculate_fie_hash(x) in cert_hashes), ['space.ssdgroup3.info.key', 'space.ssdgroup3.info.pem', 'RootCA.pem']))):
        # Get Current the current path and Append to 3x Certificate files needed for secure SSL connection
        Certificates = list(
            map(lambda x: os.getcwd() + chr(0x2f) + x, ['space.ssdgroup3.info.pem', 'space.ssdgroup3.info.key', 'RootCA.pem']))
    else:
        make_response('Invalid Certificate', 400)
else:
    make_response(MISSING_SSL_CERT, 500)
```

Good week good progress through I think I will need to try and shape the directon of the project team at next weeks meeting so we are all pullling in the same direction as this is one area of concern I have I also beginning to wish I was on the coding side as not sure my area of knowledge is being fully used doing the PM role might have to bring this up at our next meeting also need to take a look at the RAID log so we have that area of the project upto date as no point having these PM tools is they are not current and accurate. In Summary good week but still lots to do. 


**Weekly Skills Matrix New Knowledge Gained**

- [x] Code Quality
- [x] PM Documentation

**Happiness Level**
😀😀😀
