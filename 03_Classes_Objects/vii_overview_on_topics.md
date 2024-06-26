### 1. Classes and Inheritance:
   - Classes are blueprints for creating objects, and inheritance allows classes to inherit properties and methods from other classes.

`open class Shape` and `class Circle : Shape()`

### 2. Constructors:
   - Constructors are special functions that initialize objects of a class.

`class Person(val name: String, val age: Int)`

### 3. Factory Functions:
   - Factory functions are functions that create and return instances of a class.
   
   `fun createPerson(name: String, age: Int) = Person(name, age)`

### 4. Properties and Fields:
   - Properties are variables that belong to a class, and fields are the backing storage for properties.

`class Person(val name: String, var age: Int)`

### 5. Visibility Modifiers:
   - Visibility modifiers control the accessibility of classes, properties, and methods.

`private val secretCode = "1234"`

### 6. Abstract Classes:
   - Abstract classes are classes that cannot be instantiated and may contain abstract methods.
   
   `abstract class Animal { abstract fun makeSound() }`

### 7. Interfaces:
   - Interfaces define a contract of methods and properties that a class must implement.
   
   `interface Printable { fun print() }`

### 8. Delegation:
   - Delegation allows a class to delegate the implementation of an interface to another object.
   
   `class Printer(val printable: Printable) : Printable by printable`

### 9. Data Classes:
   - Data classes are classes that primarily hold data and generate useful methods like `equals()`, `hashCode()`, and `toString()`.
   
   `data class Person(val name: String, val age: Int)`

### 10. Equality:
  - Equality checks if two objects are equal based on their contents.
    
      Example: 
    ```Kotlin

    val person1 = Person("John", 25); val person2 = Person("John", 25); println(person1 == person2) // true

    ```

### 11. Destructuring:
  - Destructuring allows you to unpack the properties of an object into separate variables.

    Example:
    ```Kotlin
    val (name, age) = person1; println("Name: $name, Age: $age") // Name: John, Age: 25
    ```

### 12. Object Declarations: 
- Object declarations define singleton objects that can be accessed directly by their name.

    Example:
    ```Kotlin
    object Utils { fun printMessage() { println("Hello, world!") } }; Utils.printMessage() // Hello, world!
    ```


### 13. Enum Classes:
- Enum classes are classes that represent a fixed set of constants.

    Example:
    ```Kotlin
    enum class Color { RED, GREEN, BLUE }; val color = Color.RED
    ```
