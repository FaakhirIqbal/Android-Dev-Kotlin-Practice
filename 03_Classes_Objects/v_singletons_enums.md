## Understanding of Singletons and Enums

- Singleton classes
- Companion Objects
- Enums

### Step 1: Singleton Classes


In Kotlin, a singleton class is a class that ensures only one instance of itself is created throughout the lifecycle of the application. Singleton classes are useful when you need a single, shared instance of a class across your program.

Kotlin provides a concise way to create singleton classes using the `object` keyword. An example of a singleton class called `PlaygroundManager`:

```kotlin
object PlaygroundManager {
    val playgrounds = mutableListOf<Playground>()

    fun addPlayground(playground: Playground) {
        playgrounds.add(playground)
    }

    fun removePlayground(playground: Playground) {
        playgrounds.remove(playground)
    }

    fun getPlaygrounds(): List<Playground> {
        return playgrounds
    }
}
```

In this example:
- The `PlaygroundManager` class is declared as an `object`, indicating that it is a singleton.
- The `PlaygroundManager` singleton manages a list of `Playground` instances.
- It provides methods to add a playground (`addPlayground()`), remove a playground (`removePlayground()`), and retrieve the list of playgrounds (`getPlaygrounds()`).

To use the `PlaygroundManager` singleton, you can directly access its properties and methods:

```kotlin
val playground1 = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground2 = Playground("Block-A Sports Club", listOf("Soccer", "Volleyball"), 30)

PlaygroundManager.addPlayground(playground1)
PlaygroundManager.addPlayground(playground2)

val playgrounds = PlaygroundManager.getPlaygrounds()
println(playgrounds)
```

Output:
```
[Playground(name=Science Block Club, activities=[Basketball, Hockey, Tennis], capacity=50), Playground(name=Block-A Sports Club, activities=[Soccer, Volleyball], capacity=30)]
```

The `PlaygroundManager` singleton provides a centralized way to manage and access the list of playgrounds throughout the application.




#### Companion Objects


In Kotlin, a companion object is a singleton object that is associated with a class. It allows you to define properties and methods that belong to the class itself, rather than instances of the class.

An example of a companion object in the `Playground` class:

```kotlin
data class Playground(val name: String, val activities: List<String>, val capacity: Int) {
    companion object {
        fun createPlayground(name: String, activities: List<String>, capacity: Int): Playground {
            return Playground(name, activities, capacity)
        }
    }
}
```

- The `Playground` class has a companion object declared using the `companion object` keyword.
- Inside the companion object, we define a factory method called `createPlayground()` that takes the necessary parameters to create a new instance of the `Playground` class.
- The `createPlayground()` method returns a new instance of the `Playground` class.

To use the companion object and its factory method:

```kotlin
val playground = Playground.createPlayground("The Park Sports Club", listOf("Badminton", "Table Tennis"), 20)
println(playground)
```

Output:
```
Playground(name=The Park Sports Club, activities=[Badminton, Table Tennis], capacity=20)
```

In this example, we use the `createPlayground()` factory method from the companion object to create a new instance of the `Playground` class.

Companion objects are useful for defining utility functions, factory methods, or constants that are associated with a class but don't require an instance of the class to be accessed.

Both singleton classes and companion objects provide ways to organize and encapsulate related functionality within a class or as a standalone object. They help in creating shared resources, utility functions, or factory methods that can be accessed without creating instances of the class.



### Step 2: Create an enum

In Kotlin, an enum is a special type of class that represents a fixed set of named constants. Enums are useful when you have a predefined set of values that don't change during runtime.

An example of an enum class called `PlaygroundType`:

```kotlin
enum class PlaygroundType(val description: String) {
    INDOOR("Indoor playground"),
    OUTDOOR("Outdoor playground"),
    ADVENTURE("Adventure playground"),
    WATER("Water playground")
}
```

In this example:
- The `PlaygroundType` enum class is declared using the `enum` keyword.
- Each constant in the enum is defined as a separate object, representing a specific type of playground.
- The enum constants are `INDOOR`, `OUTDOOR`, `ADVENTURE`, and `WATER`.
- Each enum constant is associated with a `description` property, which provides a brief description of the playground type.

You can use the enum constants in your code like this:

```kotlin
val playgroundType = PlaygroundType.OUTDOOR
println(playgroundType.description) // Output: Outdoor playground

val playground = Playground("Science Block Club", listOf("Basketball", "Hockey", "Tennis"), 50, PlaygroundType.OUTDOOR)
println(playground)
```

Output:
```
Outdoor playground
Playground(name=Science Block Club, activities=[Basketball, Hockey, Tennis], capacity=50, type=OUTDOOR)
```

In this example, we create a `playground` instance with the `PlaygroundType.OUTDOOR` enum constant as the value for the `type` property.

Enums provide a way to define a set of named constants with associated values, making your code more expressive and readable.

