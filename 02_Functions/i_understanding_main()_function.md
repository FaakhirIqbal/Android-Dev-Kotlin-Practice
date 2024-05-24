## Learning the main() function

### 1. The main() Function in Kotlin

The main() function is the entry point of a Kotlin application. When you run a Kotlin program, the code inside the main() function is executed first.
```kotlin
fun main() {
    println("Hello, Kotlin!")
}
```

### 2. Functions Using the fun Keyword
In Kotlin, functions are declared using the **fun** keyword, followed by the function name, parameter list, and body.

```kotlin
fun greet(name: String): String {
    return "Hello, $name"
}

fun main() {
    println(greet("Kotlin"))
}
```
### 3. Adding Code to Run Your Program
To print "Hello, Kotlin!" using the **main()** function with arguments:
```kotlin
fun main(args: Array<String>) {
    println("Hello, Kotlin!")
}
```

### 4. Passing Arguments to main()
You can pass command-line arguments to the **main()** function using the **args** parameter.
```kotlin
fun main(args: Array<String>) {
    if (args.isNotEmpty()) {
        println("Hello, ${args[0]}")
    } else {
        println("Hello, Kotlin!")
    }
}
```
### 5. Using String Templates
Kotlin allows embedding variables or expressions inside strings using the **$** symbol and curly braces **{}** for expressions.
```kotlin
fun main(args: Array<String>) {
    val name = "Kotlin"
    println("Hello, $name")

    if (args.isNotEmpty()) {
        println("Hello, ${args[0]}")
    }
}
```
### 6. Almost Everything Has a Value
In Kotlin, most constructs (including **if** statements) are expressions and produce a value. This is different from some other languages where statements do not produce values.
```kotlin
fun main() {
    val condition = true
    val result = if (condition) "Condition is true" else "Condition is false"
    println(result)  // Prints: Condition is true
}
```
### 7. Using 'if' as an Expression
You can use the value of an 'if' expression directly because it returns a value.
**example:**
```kotlin
fun main() {
    val marksOfStudent = 60
    val isResultsExcellent = if (marksOfStudent > 90) true else false
    println(isResultsExcellent)  // Prints: false
}
```
### Complete Program
Combining all the concepts into a complete program that checks if a student qualifies for college admission based on their marks:
```kotlin
fun main(args: Array<String>) {
    // Print a welcome message with or without arguments
    if (args.isNotEmpty()) {
        println("Hello, ${args[0]}")
    } else {
        println("Hello, Kotlin!")
    }

    // Using string templates
    val name = "Kotlin"
    println("Hello, $name")

    // Checking if a student has excellent results
    val marksOfStudent = 60
    val isResultsExcellent = if (marksOfStudent > 90) true else false
    println(isResultsExcellent)  // Prints: false

    // Checking if a student qualified for college admission
    val marksOfStudent2 = 90.50
    val message = "The Student with ${if (marksOfStudent2 > 50) "Passed the entry exam" else "Unsuccessful, try again after a few days"}."
    println(message)  // Prints: The Student with Passed the entry exam.
}
```

