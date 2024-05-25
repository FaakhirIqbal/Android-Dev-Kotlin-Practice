**A. More about Kotlin functions**

**B. Default Values Functions vs Compact Functions**

## A. More about Kotlin functions

### 1. Basic Function:
```kotlin
fun greet(name: String): String {
    return "Hello, $name"
}
````

### 2. Function with Default Parameters:
```kotlin
fun greet(name: String = "Student"): String {
    return "Hello, $name"
}
```

### 3. Function Returning a Value:
```kotlin
fun add(a: Int, b: Int): Int {
    return a + b
}
```

### 4. Unit Returning Function:

```kotlin
fun printMessage(message: String) {
    println(message)
}
```

### Example
```kotlin
import java.util.*

fun randomActivity(): String {
    val activities = arrayOf("reading", "writing", "playing", "studying", "coding", "painting", "drawing")
    return activities[Random().nextInt(activities.size)]
}

fun functionName(studentName: String = randomStudentName(), activity: String = randomActivity()) {
    println("Hi Dear Student, your name is $studentName and you are doing $activity.")
}

fun randomStudentName(): String {
    val names = arrayOf("Alice", "Bob", "Charlie", "Diana", "Eve", "Frank", "Grace")
    return names[Random().nextInt(names.size)]
}

fun checkQualification(marks: Double): String {
    return when {
        marks > 90 -> "excellent"
        marks > 75 -> "very good"
        marks > 50 -> "good"
        else -> "unsatisfactory"
    }
}

fun main(args: Array<String>) {
    // Greet the student with a random name and activity
    functionName()

    // Check the student's qualification based on marks
    val marksOfStudent = 90.50
    val message = "The student has ${checkQualification(marksOfStudent)} results."
    println(message)
}
```
### Explanation

**1. Random Function:**


```randomActivity():``` Chooses a random activity from an array.

```randomStudentName():``` Chooses a random student name from an array.

**2. Function with Default Parameters:**

```functionName():``` Prints a message with the student's name and activity. If not provided, it uses random values.

**3. Using when Statement:**

```checkQualification():``` Determines the qualification message based on the student's marks using a when statement.

**4. Main Function:**

Calls ```functionName()``` to print a greeting message.
Calls ```checkQualification()``` to determine and print the student's qualification based on marks.

Using the ```when``` Statement
The ```when``` statement in Kotlin works like a ```switch-case``` in other languages but is more powerful and versatile.




## B. Default Values Functions vs Compact Functions



**1.** Kotlin allows you to set default values for function parameters, making it optional to provide arguments when calling the function.

**2.** Compact functions or single-expression functions enable you to write concise and readable code.


#### i. Function with Default Parameter Values
```kotlin
fun studentActivities(activity: String = "studying") {
    println("The student is currently $activity.")
}

fun main() {
    // Using the default parameter
    studentActivities()
    
    // Positional argument
    studentActivities("playing")
    
    // Named parameter
    studentActivities(activity = "coding in C++")
}
```

#### Output
```
The student is currently studying.
The student is currently playing.
The student is currently coding in C++.

```

#### ii. Function with Required Parameters

Let's create a ```shouldPassedExam``` function that takes three required parameters: 
```marks```, ```activitiesPerformance```, and ```iqLevel```.
We'll use a when expression to determine if the student should pass the exam based on these parameters.

```Kotlin
fun shouldPassedExam(marks: Int, activitiesPerformance: String, iqLevel: Int): Boolean {
    return when {
        marks > 85 && activitiesPerformance == "excellent" && iqLevel > 120 -> true
        marks > 70 && activitiesPerformance == "good" && iqLevel > 100 -> true
        marks > 50 && activitiesPerformance == "average" && iqLevel > 90 -> true
        else -> false
    }
}

fun main() {
    println(shouldPassedExam(90, "excellent", 130)) // true
    println(shouldPassedExam(75, "good", 110))      // true
    println(shouldPassedExam(60, "average", 95))    // true
    println(shouldPassedExam(40, "poor", 80))       // false
}
```

### 2. Compact Functions:

When a function returns the result of a single expression, you can simplify it using the ```=``` symbol.

#### i. Compact Version of studentActivities
```Kotlin
fun studentActivities(activity: String = "studying") = println("The student is currently $activity.")
```

#### ii. Compact Version of shouldPassedExam
```Kotlin
fun shouldPassedExam(marks: Int, activitiesPerformance: String, iqLevel: Int): Boolean = 
    when {
        marks > 85 && activitiesPerformance == "excellent" && iqLevel > 120 -> true
        marks > 70 && activitiesPerformance == "good" && iqLevel > 100 -> true
        marks > 50 && activitiesPerformance == "average" && iqLevel > 90 -> true
        else -> false
    }
```

#### Test Compact Functions
```Kotlin
fun main() {
    // Testing studentActivities
    studentActivities()
    studentActivities("playing")
    studentActivities(activity = "coding in C++")

    // Testing shouldPassedExam
    println(shouldPassedExam(90, "excellent", 130)) // true
    println(shouldPassedExam(75, "good", 110))      // true
    println(shouldPassedExam(60, "average", 95))    // true
    println(shouldPassedExam(40, "poor", 80))       // false
}
```




