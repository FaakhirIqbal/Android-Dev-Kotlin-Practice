## Understanding of Singletons and Enums

Sure! Let's recall the singleton class example and then explore enums in Kotlin.

### Step 1: singleton classes

In Kotlin, a singleton class is a class that ensures only one instance of itself is created throughout the lifecycle of the application. Singleton classes are useful when you need a single, shared instance of a class across your program.

Kotlin provides a concise way to create singleton classes using the `object` keyword. Here's an example of a singleton class called `PlaygroundManager`:

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
val playground1 = Playground("Central Park", listOf("Basketball", "Hockey", "Tennis"), 50)
val playground2 = Playground("Riverside Park", listOf("Soccer", "Volleyball"), 30)

PlaygroundManager.addPlayground(playground1)
PlaygroundManager.addPlayground(playground2)

val playgrounds = PlaygroundManager.getPlaygrounds()
println(playgrounds)
```

Output:
```
[Playground(name=Central Park, activities=[Basketball, Hockey, Tennis], capacity=50), Playground(name=Riverside Park, activities=[Soccer, Volleyball], capacity=30)]
```

The `PlaygroundManager` singleton provides a centralized way to manage and access the list of playgrounds throughout the application.

**Step 2: Create an enum**

In Kotlin, an enum is a special type of class that represents a fixed set of named constants. Enums are useful when you have a predefined set of values that don't change during runtime.

Here's an example of an enum class called `PlaygroundType`:

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

val playground = Playground("Central Park", listOf("Basketball", "Hockey", "Tennis"), 50, PlaygroundType.OUTDOOR)
println(playground)
```

Output:
```
Outdoor playground
Playground(name=Central Park, activities=[Basketball, Hockey, Tennis], capacity=50, type=OUTDOOR)
```

In this example, we create a `playground` instance with the `PlaygroundType.OUTDOOR` enum constant as the value for the `type` property.

Enums provide a way to define a set of named constants with associated values, making your code more expressive and readable.

