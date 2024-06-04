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

