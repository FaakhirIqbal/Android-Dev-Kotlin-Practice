## Interface Delegation in Kotlin

Interface delegation is an advanced design technique where the methods of an interface are implemented by a helper (or delegate) object. This technique is useful when you want to reuse interface functionality across multiple unrelated classes.

In Kotlin, interface delegation is supported natively, making it easy to use this pattern. Let's explore this concept using an example.


### Step 1: Make a new interface

First, let's create a new interface called `Learner` that defines a set of methods related to learning:

```kotlin
interface Learner {
    fun study()
    fun takeNotes()
    fun attendLecture()
}
```

### Step 2: Make a singleton class

Next, we'll create a singleton class called `LearningHelper` that implements the `Learner` interface:

```kotlin
object LearningHelper : Learner {
    override fun study() {
        println("Studying...")
    }

    override fun takeNotes() {
        println("Taking notes...")
    }

    override fun attendLecture() {
        println("Attending lecture...")
    }
}
```

In this example:
- The `LearningHelper` object is declared as a singleton using the `object` keyword.
- It implements the `Learner` interface and provides implementations for the `study()`, `takeNotes()`, and `attendLecture()` methods.


### Step 3: Add interface delegation

Now, let's add interface delegation to the `Student` class:

```kotlin
class Student(var name: String, var age: Int, var learner: Learner = LearningHelper) {
    fun learnNewTopic() {
        learner.study()
        learner.takeNotes()
        learner.attendLecture()
    }
}
```

In this updated `Student` class:
- We add a new property called `learner` of type `Learner`, which is initialized with the `LearningHelper` singleton object by default.
- The `learnNewTopic()` function is added, which internally calls the methods of the `Learner` interface (`study()`, `takeNotes()`, and `attendLecture()`) using the `learner` property.



### Step 4: Use interface delegation

Now, let's see how we can use interface delegation in the `Student` example:

```kotlin
fun main() {
    val student = Student("John", 20)
    student.learnNewTopic()
}
```

Output:
```
Studying...
Taking notes...
Attending lecture...
```

In the `main()` function:
- We create an instance of the `Student` class called `student`.
- We call the `learnNewTopic()` function on the `student` instance, which internally uses the `LearningHelper` object to perform the learning-related tasks.

The beauty of interface delegation is that we can easily swap out the implementation of the `Learner` interface by assigning a different object to the `learner` property of the `Student` class.
This allows for flexibility and reusability of the learning-related functionality.

For example, we can create a different implementation of the `Learner` interface and assign it to the `learner` property:

```kotlin
object AdvancedLearningHelper : Learner {
    override fun study() {
        println("Studying advanced topics...")
    }

    override fun takeNotes() {
        println("Taking detailed notes...")
    }

    override fun attendLecture() {
        println("Attending advanced lecture...")
    }
}

fun main() {
    val student = Student("John", 20, AdvancedLearningHelper)
    student.learnNewTopic()
}
```

Output:
```
Studying advanced topics...
Taking detailed notes...
Attending advanced lecture...
```

In this case, we create a new `AdvancedLearningHelper` object that provides a different implementation of the `Learner` interface. By passing `AdvancedLearningHelper` to the `Student` constructor, we can easily switch the learning behavior without modifying the `Student` class itself.

Interface delegation allows for flexible composition and reuse of functionality, making it easier to extend and customize the behavior of classes without the need for inheritance.








## Data Classes


creating a data class and explore the benefits Kotlin provides for data classes using the `Playground` data class that represents a playground where students can do activities like basketball, hockey, etc.

### Step 1: Create a data class

1. First, let's create a new package called `playground` under the `com.a1schools` package. Right-click on `com.a1schools` in the Project pane and select **New > Package**. Name the package `playground`.

2. Inside the `playground` package, create a new Kotlin file called `Playground.kt`.

3. In the `Playground.kt` file, define a data class called `Playground`:

```kotlin
data class Playground(val name: String, val activities: List<String>, val capacity: Int)
```

In above example:
- The `Playground` class is declared as a `data` class, which automatically generates some useful methods like `toString()`, `equals()`, `hashCode()`, and `copy()`.
- The `Playground` class has three properties: `name` (the name of the playground), `activities` (a list of available activities), and `capacity` (the maximum number of students allowed in the playground).



### Step 2: Use destructuring

Kotlin provides a convenient way to destructure data objects and assign their properties to individual variables using destructuring declarations.

Instead of assigning the properties one by one like this:

```kotlin
val playground = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val name = playground.name
val activities = playground.activities
val capacity = playground.capacity
```

You can use destructuring to assign the properties in a single line:

```kotlin
val (name, activities, capacity) = playground
```

This destructuring declaration assigns the `name`, `activities`, and `capacity` properties of the `playground` object to the respective variables `name`, `activities`, and `capacity`.

You can also use destructuring in a `for` loop to iterate over a collection of `Playground` objects:

```kotlin
val playgrounds = listOf(
    Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50),
    Playground("Block-A Sports Club", listOf("Soccer", "Volleyball"), 30),
    Playground("The Park Sports Club", listOf("Badminton", "Table Tennis"), 20)
)

for ((name, activities, capacity) in playgrounds) {
    println("Playground: $name, Activities: $activities, Capacity: $capacity")
}
```

Output:
```
Playground: Science Block Club, Activities: [Basketball, Hockey, Tennis], Capacity: 50
Playground: Block-A Sports Club, Activities: [Soccer, Volleyball], Capacity: 30
Playground: The Park Sports Club, Activities: [Badminton, Table Tennis], Capacity: 20
```

In this example, we create a list of `Playground` objects and use destructuring in the `for` loop to unpack the properties of each `Playground` object and print them.

The additional benefits of data classes automatically generated `toString()`, `equals()`, `hashCode()`, and `copy()` methods also apply to the `Playground` data class.

```kotlin
val playground1 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground2 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground3 = Playground("Block-A Sports Club", listOf("Soccer", "Volleyball"), 30)

println(playground1 == playground2) // true
println(playground1 == playground3) // false
```


**Automatically generated 'copy()' method:**

- Kotlin provides a `copy()` method for data classes, which allows creating a new instance of the object with some or all of its properties changed.
- The `copy()` method is useful when you need to create a modified version of an object without changing the original one.
- You can specify the properties you want to change in the `copy()` method, and the remaining properties will be copied from the original object.

```kotlin
val playground1 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground2 = playground1.copy(capacity = 60)

println(playground1) // Playground(name=Science Block Club, activities=[Basketball, Hockey, Tennis], capacity=50)
println(playground2) // Playground(name=Science Block Club, activities=[Basketball, Hockey, Tennis], capacity=60)

```

**Automatically generated 'hashCode()' method:**

In Kotlin, the `hashCode()` method is automatically generated for data classes based on their properties. The `hashCode()` method returns an integer value that represents the hash code of the object. The hash code is used to efficiently store and retrieve objects in hash-based data structures like `HashSet` or `HashMap`.
The generated `hashCode()` method for a data class takes into account the values of all the properties defined in the primary constructor. It combines the hash codes of these properties to compute a unique hash code for each instance of the data class.

```kotlin
val playground1 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground2 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground3 = Playground("Block-A Sports Club", listOf("Soccer", "Volleyball"), 30)

println(playground1.hashCode()) // Output: 1309129848
println(playground2.hashCode()) // Output: 1309129848
println(playground3.hashCode()) // Output: 1098694901
```

In this example:

We create three instances of the Playground data class: `playground1`, `playground2`, and `playground3`.
We print the hash codes of each playground instance using the `hashCode()` method.

Observations:

`playground1` and `playground2` have the same property values, so their hash codes are equal (1309129848 in this case).
`playground3` has different property values compared to `playground1` and `playground2`, resulting in a different hash code (1098694901 in this case).

The `hashCode()` method is useful when you want to use data class instances as keys in a hash-based data structure.

- Here's an example that demonstrates using the Playground instances in a HashSet:


```kotlin
val playgroundSet = HashSet<Playground>()

playgroundSet.add(playground1)
playgroundSet.add(playground2)
playgroundSet.add(playground3)

println(playgroundSet.size) // Output: 2
```
- We create a `HashSet` called `playgroundSet` to store Playground instances.
- We add `playground1`, `playground2`, and `playground3` to the `playgroundSet` using the `add()` method.
- When we print the size of `playgroundSet`, it outputs 2.


- Although we added three playground instances to the `playgroundSet`, the size of the set is 2.
- This is because `playground1` and `playground2` have the same hash code and are considered equal according to the `equals()` method (which is also automatically generated for data classes).
- The `HashSet` uses the hash code to determine the uniqueness of elements, so it treats `playground1` and `playground2` as the same element and only stores one of them.
