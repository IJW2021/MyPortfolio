![Logo](Images/Logo.png)
[1](/MyPortfolio/SEPM/Unit01.html) | [2](/MyPortfolio/SEPM/Unit02.html) | [3](/MyPortfolio/SEPM/Unit03.html) | [4](/MyPortfolio/SEPM/Unit04.html) | [5](/MyPortfolio/SEPM/Unit05.html) | [6](/MyPortfolio/SEPM/Unit06.html) | [7](/MyPortfolio/SEPM/Unit07.html) | [8](/MyPortfolio/SEPM/Unit08.html) | [9](/MyPortfolio/SEPM/Unit09.html) | [10](/MyPortfolio/SEPM/Unit10.html) | [11](/MyPortfolio/SEPM/Unit11.html) | [12](/MyPortfolio/SEPM/Unit12.html)

![Logo](Images/Diary.png)
### Week Three [Tres Sabbati]

**Forum Post**

Interesting post especially the section about code quality which is an area I know quite well. while no software is defect free according to Carnegie Mellon University's Sustainable Computing Consortium “Commercial software typically has 20 to 30 bugs for every 1,000 lines of code” (Staff Wired Magazine) it is also the case that software development cycles have shrunk with the advent of modern tooling and increased use of microservices. It used to be common for a major software release every 24 months this moved to yearly releases and now with the evergreen model (Anon) And with the increased use of automated CI/DI pipelines, code may not have the level of manual oversight it once had before being packaged and productized.

Software is also now orders of magnitude more complex than in the early days of software development. (Anon) So, we have increased complexity and smaller development cycles resulting in potentially more software defects making it into production code. However to counter this trend the technology and science of software development has also matured rapidly and the testing and SSAST tools now in use such as SonarQube , code climate etc to capture these errors are also more advance and with the new emerging technologies of machine learning now being used in the field of code analytics the future for development of high quality software is looking positive.

Tooling can only take us so far and the most important factor in delivering a product / project is still having the right people with the right skills working on the project, this can make or break a project. This is just as true now as it’s always been. From the Romans in 312bc (National Geographic 2022) building viaducts to modern Advance AI coding you need to ensure the correct skills are present in the team to successfully deliver the desired outcome.  

References 

Growth of Software Complexity in Aerospace Systems 1 | Download Scientific Diagram. [Online]. Available at: https://www.researchgate.net/figure/Growth-of-Software-Complexity-in-Aerospace-Systems-1_fig1_326997627 [Accessed 30 June 2022a].

Linux: Fewer Bugs Than Rivals | WIRED. [Online]. Available at: https://www.wired.com/2004/12/linux-fewer-bugs-than-rivals/ [Accessed 30 June 2022b].

Microsoft 365 Evergreen I.T.: What it means for you. [Online]. Available at: https://www.qa.com/about-qa/our-thinking/microsoft-365-evergreen-it-what-it-means-for-you/ [Accessed 30 June 2022c].

Roman Aqueducts | National Geographic Society. [Online]. Available at: https://education.nationalgeographic.org/resource/roman-aqueducts [Accessed 30 June 2022d].

**Meeting** 

So we have got a time now aranged with team one these time differences can be a bit of a pain so put the finishing touches to our requirements document [Requirements](/MyPortfolio/SEPM/REQUIREMENTS.pdf) It will be good to get these nailed down as its has been acting as a bit of a blocker with us not being able to progress as we dont have a detailed or even outline set of requirements. Hopfully the meeting will resolve this and we can get back on track.

**Seminar**

Spent a couple of hours writing the code for the upcoming seminar it was good to get back to writing some code after not having done it for a few weeks not 100% happy with my solution as I think the if block could be made better and if i was using Python 3.10 I would have used the new pattern matching option aka case / switch statment but my IDE only uses 3.09 so stuck with the if block implementation.

```python
# Basic COCOMO

def basic_cocomo(loc:int):
    models = [("Organic", [2.4, 1.05, 2.5, 0.38]), ("Semi-Detached", [3.0, 1.12, 2.5, 0.35]), ("Embedded", [3.6, 1.20, 2.5, 0.32])]
    lines_of_code: int = loc

    if 2 <= lines_of_code / 1000 <= 50:
        model = models[0]
    elif 50 < lines_of_code / 1000 <= 300:
        model = models[1]
    elif 300 > lines_of_code / 1000:
        model = models[2]

    effort = model[1][0] * pow(lines_of_code / 1000, model[1][1])
    time = model[1][2] * pow(effort, model[1][3])
    developers = effort / time

    print(f"The Model is {model[0]}")
    print(f"Calculated Effort is {effort}  Person-Month")
    print(f"Calculated Time is {time}  Months")
    print(f"Developers needed {developers}")


basic_cocomo(loc=4000)
```

Went back and amended the python code much happier now with how it is constructed

```python
# Basic COCOMO
from datetime import datetime
from dateutil.relativedelta import relativedelta
import sys


def basic_cocomo(loc: int) -> any:
    global model
    effort, time, developers = 0, 0, 0
    cocomo_models: list[tuple[str, list[float]]] = [("Organic", [2.4, 1.05, 2.5, 0.38]), ("Semi-Detached", [3.0, 1.12, 2.5, 0.35]), ("Embedded", [3.6, 1.20, 2.5, 0.32])]

    if isinstance(loc, int):
        lines_of_code: int = loc
    else:
        raise TypeError
    # Set the Model we are using Organic etc
    if 2 <= lines_of_code / 1000 <= 50:
        model = cocomo_models[0]
    elif 50 < lines_of_code / 1000 <= 300:
        model = cocomo_models[1]
    elif 300 > lines_of_code / 1000:
        model = cocomo_models[2]
    try:
        effort: float = model[1][0] * pow(lines_of_code / 1000, model[1][1])
        time: float = model[1][2] * pow(effort, model[1][3])
        developers: float = effort / time
    except UnboundLocalError:
        print("Input Value Cannot be Processed")

    if all(list(map(lambda x: isinstance(x, float), [effort, time, developers]))):
        print(f"\033[92mLines of code\033[96m {lines_of_code}")
        print(f"\033[92mThe Model is \033[96m{model[0]}")
        print(f"\033[92mModel Values used are \033[96m{model[1]}")
        print(f"\033[92mCalculated Effort is \033[96m{round(effort)}\033[92m Person-Month")
        print(f"\033[92mCalculated Time is \033[96m{round(time)} \033[92mMonths from current date : \033[96m {datetime.now() + relativedelta(months=+round(time)):%d/%m/%Y}")
        print(f"\033[92mDevelopers needed \033[96m{round(developers)}")
    else:
        print("Calculation Error")


# Get LOC Value from Commandline
if len(sys.argv) > 1:
    try:
        basic_cocomo(loc=int(sys.argv[1]))
    except ValueError:
        print("Invalid LOC Value")

```


**Weekly Skills Matrix New Knowledge Gained**

- [x] Estimation Methods
- [x] Refresher on Python

**Happiness Level**
😀😀😀😀😀
