![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### Week Eight [Hebdomada Octo]

![Logo](Images/Diary.png)

This week we looked at

* Look at what is meant by cryptography and examine a case study in how it can be applied to operating systems.
* Explore some common cryptographic libraries.
* Create a basic application that uses cryptographic libraries to encode sample data.

Positive but also slightly annoying start to the week on the positive side infrastructure build out is on schedule even with our change to base Operating System which is turning out to be a good decision as an our VM images have reduced in size from 150GB per VM down to about 9GB per image while storage is not a big concern our current storage array has a 8TB ZFS pool smaller is better on a security side as it means the attack surface of the OS underpinning our service is reduced.

**DR and BCP**

Along with the actual delivery we need to think about our Disaster recovery position as a solution needs to be able to recover from unforeseen events and as our domain is in a hostile environment this is important. To this regard as part of our plan is to include a backup and recovery solution as the industry leader and because there is a free tier, we have gone with a VEEAM based solution.

![Backup](Images/backup.png)

It’s also been a good week on the project broken down the project into its phases there are three main parts of our solution

* User Interface
* Data Collection
* APIs

Where possible I am going to try and align our plan with the prince2 design methodology I have used this before in my professional life and it has worked well so will be interesting to see how this transitions into a smaller project team as when I used it the team was in the hundreds.

* 1. Projects must have business justification.
* 2. Teams should learn from every stage.
* 3. Roles and responsibilities are clearly defined.
* 4. Work is planned in stages.
* 5. Project boards "manage by exception."
* 6. Teams keep a constant focus on quality.
* 7. The approach is tailored for each project.

[https://www.wrike.com/blog/project-management-basics-prince2-explained/]

As previously mentioned, I have been assigned the task of building the APIS that the rest of the solution will use while not the part of the project that has the wow factor without a strong underpinning the services that are built on top of the APIS will suffer so have been reading up on API Design the Flask Micro framework and JWT tokens. As I want to build a strong set of APIs.

We had a good discussion about encryption in the seminar which was quite interesting so after the meeting I wrote a quick ROT13 implementation which I class more of a encoding technique then a real encryption standard actually remember using it when talking part in UseNet discussion forums back in the early 90s

```python
def rot13(Input: str) -> str:
    result: list = []
    for x in Input:
        if x.isalpha():
            shift = 13 if 'Z' < x < 'n' or x < 'N' else -13
            result.append(chr(ord(x) + shift))
        else:
            result.append(x)
    return ''.join(result)
```

**GitHub Actions**
So, in an effort to save time during commits of my API code which is undergoing a period of rapid development setup a GitHub action to produce and publish the docker image this also solves another issue I was having because my main development machine is a M1 MacBook based on ARM architecture people using x86 based devices were getting problems running the docker image so getting GitHub to produce the image also resolves that issue.

```yml
name: Build and Publish

on:
  push:
    branches: [main]
  pull_request:

jobs:
  build_docker_image:
    name: Build Docker image
    runs-on: ubuntu-latest

    steps:
      - name: Checkout code
        uses: actions/checkout@v2

      - name: Set up Docker Buildx
        id: buildx
        uses: docker/setup-buildx-action@v1

      - name: Login to Github Packages
        uses: docker/login-action@v1
        with:
          registry: ghcr.io
          username: ${{ github.actor }}
          password: ${{ secrets.GHCR_PAT }}
  
      - name: Build image and push to Docker Hub and GitHub Container Registry
        uses: docker/build-push-action@v2
        with:
          context: ./Src/API/DB_Intergration/
          tags: |
            ghcr.io/uoessdgroup3/db_api:latest
          # build on feature branches, push only on main branch
          push: ${{ github.ref == 'refs/heads/main' }}

      - name: Image digest
        run: echo ${{ steps.docker_build.outputs.digest }}
```

Really enjoying playing with the GitHub actions a bit different to the GitLab CI/DI I’m use to but quite powerful what you can do with a few lines of YML automation I have a feeling is going to be a key thing in the project as if we can automate a lot of the tasks then that allow us to focus on the coding and design it’s not always about working harder sometimes you need to worker smarter by removing the barriers that prevent the developers from developing. This is a lesson I learned quite a few years ago so is something I will try to implement in our project. Will I be successful don’t know but always worth a try.  

# MariaDB

So, after making the decision to move our DMBS to maria DB due to driver issues on PostgreSQL we now needed to make MariaDB HA to do this we used a couple of methods the first was to setup replication between MariaDB hosts this was first configured as Master -> Slave but after some thought we reconfigured MariaDB to a master to master configuration that way any update on any host would be replicated. Along with this we also configured MariaDB to use SSL Certificates so the replication and any data access would be secured behind 256bit encryption

The second way was to install from source keepalived so that we could have a virtual IP for our service to connect to but in the event of a host failure the connection our service used would failover to the second host We tested this by failing on of the hosts and it failed over to the second maria DB instance and because the data had been replicated the service remained up and did not suffer an outage. 

You know when you have been reading too much on a subject when your searching takes you to bedding on the subject ISS bedding anyone? 😀 but on the whole a good positive week


![Logo](Images/Bedding.png)

Still positive about the project but I do think the size of the task we have given ourselves finally hit home this week still lots to do and not all that much time to do it but as the quote says

> “That which does not kill us makes us stronger.” 
― Friedrich Nietzsche

So, I’m going to use the pressure to motivate myself to hopefully produce a good bit of coding for the project we get one chance so put the work in and you will reep the rewards plenty of time to rest once the work is done.

**Weekly Skills Matrix New Knowledge Gained**

- [x] Encryption
- [x] YAML and Github Actions
- [x] DBMS Config and Replication

**Happiness Level**
😀😀😀😀😀
