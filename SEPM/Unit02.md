![Logo](Images/Logo.png)
[1](/MyPortfolio/SEPM/Unit01.html) | [2](/MyPortfolio/SEPM/Unit02.html) | [3](/MyPortfolio/SEPM/Unit03.html) | [4](/MyPortfolio/SEPM/Unit04.html) | [5](/MyPortfolio/SEPM/Unit05.html) | [6](/MyPortfolio/SEPM/Unit06.html) | [7](/MyPortfolio/SEPM/Unit07.html) | [8](/MyPortfolio/SEPM/Unit08.html) | [9](/MyPortfolio/SEPM/Unit09.html) | [10](/MyPortfolio/SEPM/Unit10.html) | [11](/MyPortfolio/SEPM/Unit11.html) | [12](/MyPortfolio/SEPM/Unit12.html)

![Logo](Images/Diary.png)
### Week Two [Duo]

Week two and its been a good week as have learnt some new skills though not sure the idea of naming tools and processes after vegitables is a good idea but the theory behind it has been interesting for me comming from a TDD background looking at the BDD side of things has given me some things to think about.

On the project side we had our first team meeting so need to follow up and arange a date with the other team to dicuss what requirments we will need to put into our solution. Also started making some very rough notes on what sections I want to include in our sumamry document early days but have a rough plan in my head just need to artuclate that to the other members of the team.

Also attended the first seminar good dicussion but would have been nice if a few more people could attend though being in the UK guessing its easier for me to attend then some of the other students but enjoyed the content.

**Seminar Prep Work**

Seminar 1: Requirements Gathering
The following is my Gherkin script for the task of how to use a coffee machine in this example this is based on my own coffee machine a Philips x3246 though the basic process would remain the same no matter the coffee machine being used.

Feature: Process of making a coffee using a bean to cup coffee machine in order to have a drink of coffee

```shell

Scenario: Make a latte coffee
	Given there are beans in the bean reservoir 
		And The Coffee machine is turned on
		And There is water in the water tank
		And There is milk in the milk reservoir 
		And There is a glass ready to receive coffee
		And Coffee Selector is set to latte
	When I press the Make Coffee Button
	Then I get a glass of latte Coffee
```

The Second scenario we will look at is the production of a black coffee as the coffee machine has pre-programmed programs for different coffee-based beverages,

```shell

Scenario: Make expresso 
	Given there are beans in the bean reservoir 
    		And The Coffee machine is turned on
    		And There is water in the water tank 
    		And There is a glass ready to receive coffee
    		And Coffee Selector is set to espresso
    		And Coffee strength selector button is set to high 
  	When I press the Make Coffee Button
  	Then I get a glass of expresso Italian style Coffee
```

The third scenario is running the cleaning cycle to clean the machine 

```shell
Scenario: Clean Machine
	Given That the cleaning warning light is being displayed
		And the machine is not making coffee 
		And the machine is in the cleaning mode
		And the machine is powered on
	When the play button is pressed
	Then Run the cleaning cycle program
```



**Weekly Skills Matrix New Knowledge Gained**

- [x] Gherkin
- [x] Development Types

**Happiness Level**
😀😀😀😀😀
