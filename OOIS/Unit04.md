![Logo](Image/LogoW.png)

[1](/MyPortfolio/OOIS/Unit01.html) | [2](/MyPortfolio/OOIS/Unit02.html) | [3](/MyPortfolio/OOIS/Unit03.html) | [4](/MyPortfolio/OOIS/Unit04.html) | [5](/MyPortfolio/OOIS/Unit05.html) | [6](/MyPortfolio/OOIS/Unit06.html) | [7](/MyPortfolio/OOIS/Unit07.html) | [8](/MyPortfolio/OOIS/Unit08.html) | [9](/MyPortfolio/OOIS/Unit09.html) | [10](/MyPortfolio/OOIS/Unit10.html) | [11](/MyPortfolio/OOIS/Unit11.html) | [12](/MyPortfolio/OOIS/Unit12.html)

### Week Four [Hebdomada quattuor]

![Python](Image/python-logo-master-v3-TM.png)

This week has been a python week leaning new concepts in OO design and relearning some OO design patterns from my C and C++ Days losts of creating classes class constructors using the magic __init__ method and learing more about inheretance quite a lot to take in and new ways of thinking about how to approach a problem. The OO approach opens up new ways of coding solutions to problems so in that regard enjoying the new content though having done non OO for quite a while need to unlearn some bad habits that dont fit in with the way of doinf things in the OO word

**Python OO Examples**

The Classic Person class 

```python
class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender


Person = Person('John', 23,'Male')
```

Aslo learned about the del keyword and the ability to delete a attribute from a class instance which is very cool 👍 as it allows class instances to be customised depending on the use case we want to put them to also learned about the importance of the self keyword and the use of staticmethod decorators.

```python

class Person:
    def __init__(self, name, age, gender):
        self.name = name
        self.age = age
        self.gender = gender


Person = Person('John', 23,'Male')
print(Person.__dict__)
del Person.gender
print(Person.__dict__)
```

```python
{'name': 'John', 'age': 23, 'gender': 'Male'}
{'name': 'John', 'age': 23}
```

**Weekly Skills Matrix New Knowledge Gained**

- [x] Python Classes and the init method
- [X] Python del method 
- [X] self keyword when creating classes

**Happiness Level**

😀😀😀😀
