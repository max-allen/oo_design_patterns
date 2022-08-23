<h1 align='center'>Basic Concepts</h1>

## Class
```python
class Car:
  '''Vehicle that movies from point A to B'''
  def __init__(self, seat_count, change_oil_frequency):
    self.total_mileage = 0
    self.mileage_since_change = 0
    self.change_oil = False
    self.change_oil_frequency = change_oil_frequency
    self.seat_count = seat_count

  def drive(self, miles):
    '''Moves vehicle. Conditionally updates oil change status'''
    self.total_mileage += miles
    self.mileage_since_change += miles

    if (self.should_change_oil()):
      self.change_oil = True

  def should_change_oil(self):
    '''Checks oil change status'''
    return self.mileage_since_change >= self.change_oil_frequency

  def change_oil(self):
    '''Resets oil change state'''
    self.mileage_since_change = 0
    self.change_oil = False
```

## Instance
```python
car = Car(2, 3000)

car.drive(1500)
car.should_change_oil() # False

car.drive(1500)
car.should_change_oil() # True
```

## Polymorphism
```python
class AccessibleCar(Car):
  '''Wheelchair accessible vehicle'''
  def __init__(self, seat_count, entry_type, change_oil_frequency):
    super().__init__(seat_count, change_oil_frequency)
    self.entry_type = entry_type
    self.has_lower_floor_conversion = True if entry_type == 'side' else False
    self.seat_installed = True

  def toggle_seat_status(self):
    self.seat_installed = not self.seat_installed

acc_car = AccessibleCar(4, 'side', 5000)

acc_car.seat_count # 4
acc_car.seat_count_installed # true
acc_car.toggle_seat_status()
acc_car.seat_installed # false
```

## Encapsulation
```python
class Car:
  '''Car with private instance variables'''
  def __init__(self, seat_count, change_oil_frequency):
    self.__total_mileage = 0
    self.__mileage_since_change = 0
```
Note that Python has limited support for this. See the docs on [private variables](https://docs.python.org/3/tutorial/classes.html?highlight=private#private-variables).