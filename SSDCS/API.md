![Logo](Images/Logo.png)
[1](/MyPortfolio/SSDCS/Unit01.html) | [2](/MyPortfolio/SSDCS/Unit02.html) | [3](/MyPortfolio/SSDCS/Unit03.html) | [4](/MyPortfolio/SSDCS/Unit04.html) | [5](/MyPortfolio/SSDCS/Unit05.html) | [6](/MyPortfolio/SSDCS/Unit06.html) | [7](/MyPortfolio/SSDCS/Unit07.html) | [8](/MyPortfolio/SSDCS/Unit08.html) | [9](/MyPortfolio/SSDCS/Unit09.html) | [10](/MyPortfolio/SSDCS/Unit10.html) | [11](/MyPortfolio/SSDCS/Unit11.html) | [12](/MyPortfolio/SSDCS/Unit12.html)
### API Excerise

```python
from flask import Flask
from flask_restful import Api, Resource, reqparse
 
app = Flask(__name__)
api = Api(app)
 
users = [
    {
        "name": "James",
        "age": 30,
        "occupation": "Network Engineer"
    },
    {
        "name": "Ann",
        "age": 32,
        "occupation": "Doctor"
    },
    {
        "name": "Jason",
        "age": 22,
        "occupation": "Web Developer"
    }
]
 
class User(Resource):
    def get(self, name):
        for user in users:
            if(name == user["name"]):
                return user, 200
        return "User not found", 404
 
    def post(self, name):
        parser = reqparse.RequestParser()
        parser.add_argument("age")
        parser.add_argument("occupation")
        args = parser.parse_args()
 
        for user in users:
            if(name == user["name"]):
                return "User with name {} already exists".format(name), 400
 
        user = {
            "name": name,
            "age": args["age"],
            "occupation": args["occupation"]
        }
        users.append(user)
        return user, 201
 
    def put(self, name):
        parser = reqparse.RequestParser()
        parser.add_argument("age")
        parser.add_argument("occupation")
        args = parser.parse_args()
 
        for user in users:
            if(name == user["name"]):
                user["age"] = args["age"]
                user["occupation"] = args["occupation"]
                return user, 200
        
        user = {
            "name": name,
            "age": args["age"],
            "occupation": args["occupation"]
        }
        users.append(user)
        return user, 201
 
    def delete(self, name):
        global users
        users = [user for user in users if user["name"] != name]
        return "{} is deleted.".format(name), 200
      
api.add_resource(User, "/user/<string:name>")
 
app.run(debug=True)
```
## Question One 

Run the API.py code. Take a screenshot of the terminal output. What command did you use to compile and run the code?

![Logo](Images/API1.png)

Command used to run the code contained in main.py was

```shell
/Users/ianwolloff/PycharmProjects/Excerises/venv/bin/python /Users/ianwolloff/PycharmProjects/Excerises/main.py
```

After first 

* Setting up a venv for the project
* pip install flask
* pip install flask_restful

## Question Two

Run the following command at the terminal prompt: w3m http://127.0.0.1:5000/user/Ann

As my code development is taking place on OSX we can replace the w3m command for the curl command but the outcome is the same when run the following out put is produced

```json
{
    "name": "Ann",
    "age": 32,
    "occupation": "Doctor"
}
```

The reason why we get this output is down to the folloing block of code

```python
    def get(self, name):
        for user in users:
            if (name == user["name"]):
                return user, 200
        return "User not found", 404
```
 
 because the request we are making is a standard get request we execute the get block above and because the name we are passing "Ann" exists in the users list defined in the code the validation in the if statment passes and we return the Ann user dictonary with a http code of 200 success.
 
## Question Three

Run the following command at the terminal prompt: w3m http://127.0.0.1:5000/user/Adam What happens when this command is run, and why?

When we run the following command **curl http://127.0.0.1:5000/user/Adam** we get the folloing output "User not found" the reason for this is the if statment in the get function if the name passed does not exist in the user list made up of James Ann Jason then the return contained in the if block will not fire and insted the "User not found" value will be returned along with a http status code of 404 (Not Found) 

## Question Four

What capability is achieved by the flask library?

The capability the flask library is it removes abstracts the low level socket programming required to handle the http requests made to the api code if this was not the case then as developers we would have to deal with low level sockets datagrams packets and protocols for network comunication. the flask library handles these functions and presents them to the developer as a series of classes and methods.

This then allows the develoepr to focus on the sevices they are trying to deliver in their application rather then the mechnicism of delivery



