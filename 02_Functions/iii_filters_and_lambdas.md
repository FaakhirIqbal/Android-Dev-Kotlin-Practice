## Filters and Lambdas in Kotlin

Filters are used to select elements from a collection based on a condition. 

Lambdas are anonymous functions that can be used to pass behavior as a parameter.

### Creating a Filter

Suppose we have a list of students' marks, and we want to filter out the marks that are above a certain threshold.
```Kotlin
fun main() {
    val marks = listOf(95, 85, 70, 65, 90, 45, 80)
    val passingMarks = marks.filter { it > 75 }
    println(passingMarks)  // Output: [95, 85, 90, 80]
}
```

### Eager vs Lazy Filters
#### Eager Filters

An eager filter processes the entire collection and creates a new list immediately.
```kotlin

fun main() {
    val marks = listOf(95, 85, 70, 65, 90, 45, 80)
    val passingMarks = marks.filter { it > 75 }
    println(passingMarks)  // Output: [95, 85, 90, 80]
}

```
#### Lazy Filters

A lazy filter uses a ```Sequence```, which processes elements one by one and can transform them on-the-fly, without creating a new list until needed.

```Kotlin
fun main() {
    val marks = listOf(95, 85, 70, 65, 90, 45, 80)
    val passingMarks = marks.asSequence().filter { it > 75 }
    println(passingMarks.toList())  // Output: [95, 85, 90, 80]
}

```

#### Using lazyMap
lazyMap refers to applying a transformation lazily to each element of a sequence.

```Kotlin
fun main() {
    val marks = listOf(95, 85, 70, 65, 90, 45, 80)
    val passingMarks = marks.asSequence().filter { it > 75 }.map { it + 5 }
    println(passingMarks.toList())  // Output: [100, 90, 95, 85]
}
```
#### comprehensive example:

```Kotlin
data class Student(val name: String, val marks: Int, val activity: String)

fun main() {
    val students = listOf(
        Student("Alice", 95, "basketball"),
        Student("Bob", 85, "chess"),
        Student("Charlie", 70, "football"),
        Student("Diana", 65, "reading"),
        Student("Eve", 90, "swimming"),
        Student("Frank", 45, "basketball"),
        Student("Grace", 80, "dancing")
    )

    // Eager filter: create a new list immediately
    val highScorersEager = students.filter { it.marks > 75 }
    println("Eager Filter: $highScorersEager")

    // Lazy filter: use a sequence
    val highScorersLazy = students.asSequence().filter { it.marks > 75 }
    println("Lazy Filter: ${highScorersLazy.toList()}")

    // Lazy map: transform elements on-the-fly
    val highScorersLazyMap = students.asSequence()
        .filter { it.marks > 75 }
        .map { it.copy(marks = it.marks + 5) }
    println("Lazy Map: ${highScorersLazyMap.toList()}")
}
```

**Eager Filter:**

Creates a new list of students who scored more than 75 marks.
filter { it.marks > 75 } immediately processes the list and creates a new list.

**Lazy Filter:**

Uses asSequence() to create a sequence, which processes elements one by one.
filter { it.marks > 75 } is applied lazily, and toList() is called to create the final list when needed.

**Lazy Map:**

Transforms the filtered elements on-the-fly using map { it.copy(marks = it.marks + 5) }.
This example adds 5 marks to each high-scoring student.


**Output results:**
```
Eager Filter: [Student(name=Alice, marks=95, activity=basketball), Student(name=Bob, marks=85, activity=chess), Student(name=Eve, marks=90, activity=swimming), Student(name=Grace, marks=80, activity=dancing)]
Lazy Filter: [Student(name=Alice, marks=95, activity=basketball), Student(name=Bob, marks=85, activity=chess), Student(name=Eve, marks=90, activity=swimming), Student(name=Grace, marks=80, activity=dancing)]
Lazy Map: [Student(name=Alice, marks=100, activity=basketball), Student(name=Bob, marks=90, activity=chess), Student(name=Eve, marks=95, activity=swimming), Student(name=Grace, marks=85, activity=dancing)]
```


