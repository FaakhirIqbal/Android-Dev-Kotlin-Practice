## Understanding Nullability in Kotlin 

#### 1. Non-Nullable Variables:
By default, variables in Kotlin cannot be null. If you declare a variable without specifying that it can be null,
Kotlin will assume it is non-nullable.

```kotlin
var nonNullableInt: Int = 10
nonNullableInt = null // This line will cause a compile-time error
```

#### 2. Nullable Variables:
To allow a variable to hold a null value, you need to explicitly declare it as nullable by appending a question mark **(?)** to its type.

```kotlin
var nullableInt: Int? = 10
nullableInt = null // This is allowed
```

How to declare an Int variable and assign null to it using Kotlin's null safety features.

```kotlin
fun main() {
    // Non-nullable Int variable
    var nonNullableInt: Int = 10
    // nonNullableInt = null // Uncommenting this line will cause a compile-time error

    // Nullable Int variable
    var nullableInt: Int? = 10
    println("Nullable Int before assigning null: $nullableInt")

    // Assigning null to the nullable variable
    nullableInt = null
    println("Nullable Int after assigning null: $nullableInt")

    // Using safe call operator to avoid null pointer exception
    val length: Int? = nullableInt?.toString()?.length
    println("Length of nullableInt as string: $length")

    // Using Elvis operator to provide a default value
    val safeLength: Int = nullableInt?.toString()?.length ?: 0
    println("Safe length with Elvis operator: $safeLength")
}
```
#### Explanation
#### 1. Non-nullable Variable:

```kotlin
var nonNullableInt: Int = 10
```
The variable **'nonNullableInt'** is declared as an **'Int'** and assigned a value of 10.
Attempting to assign **'null'** to it will result in a compile-time error.

#### 2. Nullable Variable:

```kotlin
var nullableInt: Int? = 10
nullableInt = null
```
The variable **nullableInt** is declared as a nullable **'Int'    'Int?'**. It is initially assigned a value of 10 and then assigned **'null'**, which is allowed.

#### 3. Safe Call Operator:

```kotlin
val length: Int? = nullableInt?.toString()?.length

```
The safe call operator **'?.'** is used to safely access properties and methods on a nullable variable. If **nullableInt** is **null**, the entire expression evaluates to **null** without throwing a **NullPointerException**.


#### 4. Elvis Operator:
```kotlin
val safeLength: Int = nullableInt?.toString()?.length ?: 0

```

The Elvis operator **?:** provides a default value if the expression on its left is **null**. In this case, if **nullableInt** is **null**, the **safeLength** variable will be assigned a value of 0.


#### 5. Double-bang Operator:

```kotlin
val forceLength: Int = nullableInt!!.toString().length

```
The double-bang operator **!!** converts a **nullable** variable to a **non-nullable** type. If **nullableInt** is **null**, this will throw a **KotlinNullPointerException**. In the example, this operation is enclosed in a **try-catch** block to handle the potential exception.



## Understanding Arrays, Lists, and Loops in Kotlin

### Arrays in Kotlin

An array in Kotlin is a collection of elements that can be accessed by an index. Arrays in Kotlin are represented by the **Array** class, and there are specialized classes for primitive types, such as **IntArray**, **DoubleArray**, etc.

Declaring an Array
You can declare an array using the **arrayOf** function, or for primitive types, you can use functions like **intArrayOf**, **doubleArrayOf**, etc.

```kotlin
fun main() {
    // Declare an array using arrayOf
    val programmingLanguages = arrayOf("Java", "Python", "GO", "C++", "Swift")

    // Print the array
    println("Array: ${programmingLanguages.joinToString()}")
    
    // Accessing elements by index
    println("First element: ${programmingLanguages[0]}")
    println("Last element: ${programmingLanguages[programmingLanguages.size - 1]}")
    
    // Modifying an element
    programmingLanguages[1] = "JavaScript"
    println("After modification: ${programmingLanguages.joinToString()}")
    
    // Using a for loop to iterate over the array
    println("Using a for loop:")
    for (language in programmingLanguages) {
        println(language)
    }

    // Using forEach to iterate over the array
    println("Using forEach:")
    programmingLanguages.forEach { language ->
        println(language)
    }
}
```

**Explanation**

* **arrayOf:** Creates an array containing the specified elements.
* **joinToString:** Converts the array to a string with each element separated by a comma.
* **indexing:** Accesses or modifies an element at the specified index.
* **for loop and forEach:** Iterates over the elements of the array.

Running this code will output:
```
Array: Java, Python, GO, C++, Swift
First element: Java
Last element: Swift
After modification: Java, JavaScript, GO, C++, Swift
Using a for loop:
Java
JavaScript
GO
C++
Swift
Using forEach:
Java
JavaScript
GO
C++
Swift
```



### Lists in Kotlin

Kotlin provides two types of lists:

**Immutable List:** Created using **listOf**.

**Mutable List:** Created using **mutableListOf**.




#### 1. Immutable List:
An **immutable list** is **read-only**, meaning you cannot add or remove elements after its creation.


```kotlin
fun main() {
    // Declare an immutable list using listOf
    val programmingLanguages = listOf("Java", "Python", "GO", "C++", "Swift")
    
    // Print the list
    println("Immutable list: $programmingLanguages")
}

```
#### Explanation:
**listOf:** Creates a read-only list containing the specified elements.

**println:** Prints the list to the console.


Running this code will output:
```
Immutable list: [Java, Python, GO, C++, Swift]

```

#### 2. Mutable List:
A **mutable list** allows you to add, remove, and update elements after its creation.

#### Example:
```kotlin
fun main() {
    // Declare a mutable list using mutableListOf
    val programmingLanguages = mutableListOf("Java", "Python", "GO", "C++", "Swift")
    
    // Print the initial list
    println("Initial mutable list: $programmingLanguages")
    
    // Add an element to the list
    programmingLanguages.add("Kotlin")
    println("After adding Kotlin: $programmingLanguages")
    
    // Remove an element from the list
    programmingLanguages.remove("GO")
    println("After removing GO: $programmingLanguages")
    
    // Update an element in the list
    programmingLanguages[1] = "JavaScript"
    println("After updating Python to JavaScript: $programmingLanguages")
}
```
**Explanation**


**mutableListOf:** Creates a mutable list that allows modification.
**add:** Adds a new element to the end of the list.
**remove:** Removes the first occurrence of the specified element from the list.
**indexing:** Updates the element at the specified index.


Code output:
```
Initial mutable list: [Java, Python, GO, C++, Swift]
After adding Kotlin: [Java, Python, GO, C++, Swift, Kotlin]
After removing GO: [Java, Python, C++, Swift, Kotlin]
After updating Python to JavaScript: [Java, JavaScript, C++, Swift, Kotlin]
```

#### Arrays vs. Lists
**Arrays:** Fixed-size collection of elements. Once an array is created, its size cannot be changed.
**Lists:** Size can be changed dynamically (mutable lists). Lists can be either **immutable** or **mutable**.


### Using Loops with Lists
Kotlin provides several ways to iterate over elements in a list using loops.

```kotlin
fun main() {
    val programmingLanguages = listOf("Java", "Python", "GO", "C++", "Swift")

    // Using a for loop
    println("Using a for loop:")
    for (language in programmingLanguages) {
        println(language)
    }

    // Using forEach
    println("\nUsing forEach:")
    programmingLanguages.forEach { language ->
        println(language)
    }

    // Using forEachIndexed
    println("\nUsing forEachIndexed:")
    programmingLanguages.forEachIndexed { index, language ->
        println("Element at index $index is $language")
    }
}
```

**Explanation**

**for loop:** Iterates over each element in the **list**.
**forEach:** Higher-order function that applies the given lambda to each element in the **list**.
**forEachIndexed:** Similar to **forEach**, but also provides the index of each element.

Running this code will output:
```
Using a for loop:
Java
Python
GO
C++
Swift

Using forEach:
Java
Python
GO
C++
Swift

Using forEachIndexed:
Element at index 0 is Java
Element at index 1 is Python
Element at index 2 is GO
Element at index 3 is C++
Element at index 4 is Swift
```


