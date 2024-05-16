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
