**Python** is an *Object Oriented Programming Language*.

For example we can make a class in a python file called Employees.py:

```Python
#!/bin/python3

class Employees:
	def __init__(self, name, department, role, salary, years_employed):
		self.name = name
		self.department = department
		self.role = role
		self.salary = salary
		self.years_employed = years_employed

	def eligible_for_retirement:
		if self.years_employed >= 20:
			return True
		else:
			return False
```

All classes have an *init* function which is executed when the class is being initiated 

Then we can now make another python file to access this class. Lets name this ouremployees.py

```Python
#!/bin/python3

from Employees import Employees

e1 = Employees("Bob", "Sales", "Director of Sales", 100000, 20)
e2 = Employees("Linda", "Executive", "CIO", 150000, 10)

print(e1.name) #outputs Bob
print(e1.eligible_for_retirement) #outputs True
```

We can use this Object Oriented Programming knowledge to build a Shoe Budget Tool

First lets create a class function called Shoes.py:

```Python
#!/bin/python3

class Shoes: 
	def __init__(self, name, price): 
		self.name = name 
		self.price = float(price) 
		
	def budget_check(self, budget): 
		if not isinstance(budget, (int, float)): 
			print('Invalid entry. Please enter a number.') 
			exit() 
			
	def change(self, budget): 
		return (budget - self.price) 
		
	def buy(self, budget): 
		self.budget_check(budget) 
		
		if budget >= self.price: 
			print(f'You can cop some {self.name}') 
			
			if budget == self.price: 
				print('You have exactly enough money for these shoes.') 
				
			else: 
				print(f'You can buy these shoes and have ${self.change(budget)}  
				left over') 
				
		exit('Thanks for using our shoe budget app!')
```

Now, lets create the python file that will import this class:

```Python
#!/bin/python3

from Shoes import Shoes 

low = Shoes('And 1s', 30) 
medium = Shoes('Air Force 1s', 120) 
high = Shoes('Off Whites', 400) 

try: 
	shoe_budget = float(input('What is your shoe budget? ')) 
except ValueError: 
	exit('Please enter a number') 

for shoes in [high, medium, low]: 
	shoes.buy(shoe_budget)
```
