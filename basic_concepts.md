<center>Basic Concepts</center>

---
### Class
```python
class Car:
  '''Vehicle that movies from point A to B.'''
  def __init__(self, make, model, year):
    self.make = make
    self.model = model
    self.year = year
    self.total_mileage = 0
    self.mileage_since_change = 0
    self.change_oil = False
    self.change_oil_frequency = 3000

  def drive(self, miles):
    self.total_mileage += miles
    self.mileage_since_change += miles
    if (self.should_change_oil()):
      self.change_oil = True

  def should_change_oil(self):
    return self.mileage_since_change >= self.change_oil_frequency

  def change_oil(self):
    self.mileage_since_change = 0
    self.change_oil = False

car = Car('mercedes', 'GLE-class', 2022)

car.drive(1500)
car.should_change_oil() # False

car.drive(1500)
car.should_change_oil() # True
```

### Class Instance
```python
car = Car('mercedes', 'GLE-class', 2022)

car.drive(1500)
car.should_change_oil() # False

car.drive(1500)
car.should_change_oil() # True
```
