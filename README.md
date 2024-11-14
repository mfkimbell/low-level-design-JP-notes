# low-level-design-JP-notes

## Java vs Python: Calling Superclass Methods

#### Java Example
```java
class Food {
    public String getFood() {
        return "Sandwich";
    }
}

class PackagedFood extends Food {
    @Override
    public String getFood() {
        return super.getFood() + " in a bag";
    }
}
```

#### Python Example
```python
class Food:
    def get_food(self) -> str:
        return "Sandwich"

class PackagedFood(Food):
    def get_food(self) -> str:
        return super().get_food() + " in a bag"
```

### Python Constructor Initialization
```python
class Base:
    def __init__(self):
        print("Base constructor called")

class Derived(Base):
    def __init__(self):
        super().__init__()  # Calls the constructor of Base class
        print("Derived constructor called")
```

#### Summary
- **Java**: Use `super.methodName()` to call superclass methods; `super()` for constructors.
- **Python**: Use `super().method_name()` to call superclass methods or `super().__init__()` for constructors.

## Summary
- **Java**: Use `this` to refer to instance variables and methods. Use `super()` to call superclass constructors. Private variables are commonly used to enforce encapsulation.
- **Python**: Use `self` to refer to instance variables and methods. Use `super()` to call superclass methods or constructors.

#### Constructor and Method Example Java
```java
class Person {
    private String name;  // Private variable declaration
    private int age;  // Another instance variable to differentiate

    public Person(String name, int age) {
        this.name = name;  // Use `this` to refer to the instance variable
        this.age = age;    // Use `this` to refer to the instance variable
    }

    public void printDetails() {
        System.out.println("Name: " + this.name + ", Age: " + this.age);  // Use `this` to refer to instance variables
    }
}

```
#### Constructor and Method Example Python
```python
class Person:
    def __init__(self, name: str, age: int):
        self.name = name  # Use `self` to refer to the instance variable
        self.age = age    # Another instance variable to differentiate

    def print_details(self):
        print(f"Name: {self.name}, Age: {self.age}")  # Use `self` to refer to instance variables
```

# Python

The single underscore (_) before a variable name (like self._rows and self._columns) is a Python convention that indicates the variable is intended to be private or protected and should not be accessed directly from outside the class.

Same goes for methods if i did `_initGrid()` that might indicate that the method should not be called from outside the class, which enforces that it should be used only as part of the class’s internal setup. Because it's public, we might initialized the grid at anytime from another method. 

```python
class Grid:
    def __init__(self, rows, columns):
        self._rows = rows
        self._columns = columns
        self._grid = [[GridPosition.EMPTY for _ in range(columns)] for _ in range(rows)]
        self.initGrid()
```
