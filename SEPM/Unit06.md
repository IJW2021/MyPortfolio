![Logo](Images/Logo.png)
[1](/MyPortfolio/SEPM/Unit01.html) | [2](/MyPortfolio/SEPM/Unit02.html) | [3](/MyPortfolio/SEPM/Unit03.html) | [4](/MyPortfolio/SEPM/Unit04.html) | [5](/MyPortfolio/SEPM/Unit05.html) | [6](/MyPortfolio/SEPM/Unit06.html) | [7](/MyPortfolio/SEPM/Unit07.html) | [8](/MyPortfolio/SEPM/Unit08.html) | [9](/MyPortfolio/SEPM/Unit09.html) | [10](/MyPortfolio/SEPM/Unit10.html) | [11](/MyPortfolio/SEPM/Unit11.html) | [12](/MyPortfolio/SEPM/Unit12.html)

![Logo](Images/Diary.png)
### Week Six [Hebdomada Sex]

Spent a couple of hours looking at pytest its a lot nicer then unittest so may use this in all my projects now part of the excerise was to take some unit tests and make them fail. Must admit never been asked before to make a test fail first thought was ok look at the edge cases as we are dealing with money I thought lets look at what happens if we introduce a negtive number for this I added to the main class so we could capture an exception in regard to negitive numbers 

```python
"""
New Type to raise Exception on Negitive Values
"""

class ValueLessThenZero(Exception):
    pass
```

The first test was simple get the wallet amount and ensure it was zero the default value

```python
def test_default_initial_amount():
    wallet = Wallet()
    assert wallet.balance == 0
```

We can make this fail by overiding the __init__ constructor initial_amoun parameter by passing in a value to the constructor

```python
def test_default_initial_amount(20):
    wallet = Wallet()
    assert wallet.balance == 0
```

In this example we have passed in 20 to the constructor so in the class self.balance will now evaluate to 20 rather then 0 meaning the assertion that the balance is zero will now fail.

The second test sets the value to 100 and then checks that the value returned is 100

```python
def test_setting_initial_amount():
    wallet = Wallet(100)
    assert wallet.balance == 100
```

we can make this test fail by passing in any value that is not 100 for example

```python
def test_setting_initial_amount():
    wallet = Wallet(50)
    assert wallet.balance == 100
```
    
the 3rd test builds a wallet with a value of 10 and then calls the add_cash method to add 90 to it the assert then checks that the value is 100 90+10

```python
def test_wallet_add_cash():
    wallet = Wallet(10)
    wallet.add_cash(90)
    assert wallet.balance == 100
```

as in the previous example we can fail the test by changing either the constructor value or the method call so that the result does not eaqual 100 or by chnaging the sign of the add cash value to negitive -90 as the function does not do any input validation to ensure that the add cash parameter is not a negitive number

```python

    def add_cash(self, amount):
        self.balance += amount
```

we can rewrite this to add validation

```python
    def add_cash(self, amount):
        if amount >= 0:
            self.balance += amount
        else:
            raise ValueLessThenZero
```

For the next test we can again change any of the two values in this case we have set the wallet amount to 30 so when 10 is removed the value left is not 10 so the test will fail

```python
def test_wallet_spend_cash():
    wallet = Wallet(30)
    wallet.spend_cash(10)
    assert wallet.balance == 10
```

in the final test if 

```python
def test_wallet_spend_cash_raises_exception_on_insufficient_amount():
    wallet = Wallet()
    with pytest.raises(InsufficientAmount):
        wallet.spend_cash(100)
```

if we remove the exception catch block the test will then fail

```python 
def test_wallet_spend_cash_raises_exception_on_insufficient_amount():
    wallet = Wallet()
    wallet.spend_cash(100)
```

![Logo](Images/PYERROR.png)

Interesting seminar topic and good to hear Lukmans insight into the UX design proceess my forum post for the semianr was

## Forum Post

After having a think about the paper while the model in question I think was a good model for 2007/2008 the problem with it however is the software landscape has changed considerably in the 14 years since the model was published. This model was looking at the single user experience where what we should look at now is how the experience of a user fits into a wider modern ecosystem of linked products and services.

If we think about this in the context of software, consumers are now more advance than they were back in 2007/2008 they now want and demand a unified experience across their software , hardware and services this removes a large part of the model as emotional responses will be changed for people already within an ecosystem the product belongs to. 

The experience they will show is not directly attributed to their interaction with the product but also inherited from their previous experience of interacting with the common elements across the platform ecosystem. When a user receives a new product or interacts with a new service, they will already have an expectation of how that product will operate based on their exposure to other products and services within the same family of products within the eco system. An example of this are the three big ICT ecosystems

*     Microsoft

*     Google

*     Apple

A user who Is already in and invested in time and money in one of these eco systems and then receives a new application or uses a new service will already have an preconceived idea on how that service will operate and how the system will behave without ever seeing the new product or service. 

So, their response both emotional and non-emotional is dictated both by the product or service they are using but also by their past experience within the ecosystem the product belongs to. This has both advantages and disadvantages. The plus is for a user the time taken to adopt a new product is reduced and there is usually a high degree of interoperability between products and services in the same ecosystem. The downside from the consumer point of view is these ecosystems tend to be walled gardens and once a user is investigated in a set of products and services from one ecosystem it is often very hard to move to another without considerable effort or expense.

The standard IT Eco-System can be split into four pillars each of these generating a response from a user when experiencing use of a product or service.

1. Platform (OS Level)

2. Hardware

3. Applications

4. Services

(Anon)

So what I would add to the Model is an Ecosystem / Prior Experience section to cover off pre-existing expectations based on the use of associated services and products. 

References

Apple SWOT Analysis (5 Key Strengths in 2021). [Online]. Available at: https://strategicmanagementinsight.com/swot-analyses/apple-swot-analysis/ [Accessed 20 July 2022].

David G. Messerschmitt and Clemens Szyperski. 2003. Software Ecosystem: Understanding an Indispensable Technology and Industry. MIT Press, Cambridge, MA, USA.



**Weekly Skills Matrix New Knowledge Gained**

- [x] 
- [x] 

**Happiness Level**
😀😀😀😀😀
