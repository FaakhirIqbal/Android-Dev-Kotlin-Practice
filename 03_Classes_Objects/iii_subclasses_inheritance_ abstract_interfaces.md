## 1. Subclasses and Inheritance

In Kotlin, inheritance is a mechanism that allows a class to inherit properties and methods from another class. The class that inherits is called the subclass or derived class, and the class being inherited from is called the superclass or base class.

By default, classes in Kotlin are `final`, which means they cannot be subclassed. To allow a class to be subclassed, you need to mark it as `open`.

Let's say we have a base class called `Person` that represents a general person:

```kotlin
open class Person(var name: String, var age: Int) {
    open fun introduce() {
        println("Hi, my name is $name and I'm $age years old.")
    }
}
```

In this example, the `Person` class is marked as `open`, allowing it to be subclassed. It has two properties, `name` and `age`, and an `open` function called `introduce()` that prints an introduction message.

Now, let's create a subclass called `Student` that inherits from the `Person` class:

```kotlin
class Student(name: String, age: Int, var studentId: String, var grade: String) : Person(name, age) {
    override fun introduce() {
        super.introduce()
        println("I am a student with ID $studentId in grade $grade.")
    }
}
```

In this subclass:
- The `Student` class extends the `Person` class using the `: Person(name, age)` syntax, indicating that it inherits from `Person` and passes the `name` and `age` parameters to the `Person` constructor.
- The `Student` class adds two additional properties: `studentId` and `grade`, which are specific to a student.
- The `introduce()` function is overridden in the `Student` class using the `override` keyword. This allows the subclass to provide its own implementation of the function.
- Inside the overridden `introduce()` function, we call `super.introduce()` to invoke the superclass's implementation of `introduce()`, which prints the basic introduction message.
- After that, we print additional information specific to the student, including their `studentId` and `grade`.

Now, let's see how we can use the `Student` subclass:

```kotlin
fun main() {
    val person = Person("John", 25)
    person.introduce()

    val student = Student("Alice", 20, "12345", "10th")
    student.introduce()
}
```

Output:
```
Hi, my name is John and I'm 25 years old.
Hi, my name is Alice and I'm 20 years old.
I am a student with ID 12345 in grade 10th.
```

In the `main()` function:
- We create an instance of the `Person` class called `person` and call its `introduce()` function, which prints the basic introduction message.
- We create an instance of the `Student` class called `student`, providing the necessary parameters for `name`, `age`, `studentId`, and `grade`.
- We call the `introduce()` function on the `student` instance, which first calls the superclass's implementation to print the basic introduction, and then prints the additional student-specific information.

This example demonstrates how subclasses and inheritance work in Kotlin. The `Student` class inherits the properties and methods of the `Person` class and can override and extend its behavior as needed.

Remember to use the `open` keyword on the base class and any properties or functions that you want to allow subclasses to override. This helps maintain control over which parts of the class can be extended and overridden.



## 2. Abstract Classes

An abstract class is a class that cannot be instantiated directly and may contain abstract properties or methods without an implementation. It serves as a base for other classes to inherit from and provides a common definition for its subclasses.

Here's an example of an abstract class `Student`:

```kotlin
abstract class Student(var name: String, var age: Int) {
    abstract fun attendClass()
    
    fun submitHomework() {
        println("$name submitted the homework.")
    }
}
```

In this example:
- The `Student` class is declared as `abstract`, indicating that it cannot be instantiated directly.
- It has two properties: `name` and `age`, which are common to all students.
- The `attendClass()` function is declared as `abstract`, meaning it doesn't have an implementation in the `Student` class and must be overridden by its subclasses.
- The `submitHomework()` function is a non-abstract function with a default implementation that can be optionally overridden by subclasses.

Now, let's create a subclass `UndergraduateStudent` that inherits from the `Student` abstract class:

```kotlin
class UndergraduateStudent(name: String, age: Int, var major: String) : Student(name, age) {
    override fun attendClass() {
        println("$name is attending an undergraduate class.")
    }
}
```

In this subclass:
- The `UndergraduateStudent` class extends the `Student` abstract class and provides a constructor that takes `name`, `age`, and `major` as parameters.
- It overrides the `attendClass()` function and provides its own implementation specific to undergraduate students.


## 3. Interfaces

An interface is a contract that specifies a set of abstract methods and properties that a class can implement. It defines the behavior that a class must exhibit without specifying the implementation details.

Here's an example of an interface `Learner`:

```kotlin
interface Learner {
    fun study()
    fun takeExam()
}
```

In this example:
- The `Learner` interface declares two abstract methods: `study()` and `takeExam()`.
- Any class that implements the `Learner` interface must provide implementations for these methods.

Now, let's create a class `GraduateStudent` that implements the `Learner` interface:

```kotlin
class GraduateStudent(var name: String, var researchArea: String) : Learner {
    override fun study() {
        println("$name is studying advanced topics in $researchArea.")
    }
    
    override fun takeExam() {
        println("$name is taking a graduate-level exam.")
    }
}
```

In this class:
- The `GraduateStudent` class implements the `Learner` interface and provides implementations for the `study()` and `takeExam()` methods.
- It has its own properties `name` and `researchArea` specific to graduate students.

### Comparison between Abstract classes and Interfaces
- Abstract classes are used when you want to define a base class that contains some common functionality and properties, but also allows subclasses to provide their own implementations for certain methods.
- Interfaces are used to define a contract or a set of behaviors that a class must adhere to, without specifying the implementation details.
- A class can inherit from only one abstract class, but it can implement multiple interfaces.
- Abstract classes can have both abstract and non-abstract methods and properties, while interfaces can only have abstract methods and properties.





