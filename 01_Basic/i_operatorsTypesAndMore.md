## Introduction

In this lab, you will learn the basics of the Kotlin programming language, including data types, operators, variables, control structures, and the difference between nullable and non-nullable variables.

## What should we already know

Before proceeding, you should be familiar with the following:

- Creating a project in IntelliJ IDEA.
- Opening and executing code in Kotlin's REPL (Read-Eval-Print Loop) in IntelliJ IDEA (Tools > Kotlin > Kotlin REPL).

## What you'll learn

By completing this lab, you will gain knowledge and skills in the following areas:

- Using Kotlin data types, operators, and variables.
- Working with booleans and conditions.
- Understanding nullable and non-nullable variables.
- Implementing arrays, lists, and loops in Kotlin.

## What we'll do

Will work with the Kotlin REPL to learn and practice the basics of Kotlin.



### 1. Variables and Basic Data Types
```kotlin
// Basic Data Types and Variables
  val number = 10
  val decimalNumber = 3.14
  val character = 'A'
  val text = "Hello, Kotlin!"
  println(number)
  println(decimalNumber)
  println(character)
  println(text)
 ```

### 2. Practice using types (Int, Long, ToByte, etc.)
```kotlin
val intValue = 10 // Int
val longValue = 1000000000000L // Long
val byteValue: Byte = 5 // Byte

println(intValue)
println(longValue)
println(byteValue)
```
- **intValue** is of type **Int**, **longValue** is of type **Long**, and **byteValue** is of type **Byte**
- The **L** suffix is used to explicitly specify a **Long** value.
- The : **Byte** syntax is used to explicitly specify the type for **byteValue**.




### 3. The value of variable types
```kotlin
// Using 'val' to declare variables
val number = 10
val text = "Hello"

println(number)
println(text)

// Uncommenting the line below would result in an error
// number = 20 // Error: val cannot be reassigned

// Using 'var' to declare variables
var mutableNumber = 10
var mutableText = "Hello"

println(mutableNumber)
println(mutableText)
// mutableNumber and mutableText are declared using var,
// so reassigning them (mutableNumber = 20, mutableText = "Hi") is allowed and does not result in an error.

// Reassigning variables declared with 'var' is allowed
mutableNumber = 20
mutableText = "Hi"

println(mutableNumber)
println(mutableText)

```
- In Kotlin, variables declared with **val** are **immutable**, meaning their values cannot be changed once assigned. They can only be initialized once.
- In the original **val** example, number and text are declared using **val**, so attempting to reassign them (**number = 20**) results in an error.
- Variables declared with **var** are **mutable**, meaning their values can be changed after initialization, so (**mutableNumber = 20**, **mutableText = "Hi"**) is allowed.


### 4. Strings and Characters
```kotlin
val singleQuoteChar = 'A'
val doubleQuoteString = "Hello, Kotlin!"

println(singleQuoteChar)
println(doubleQuoteString)
```
- **singleQuoteChar** holds a single character, **'A'**, which is enclosed in single quotes.
- **doubleQuoteString** holds a string, **"Hello, Kotlin!"**, which is enclosed in double quotes.
- Both single quotes (**'**) and double quotes (**"**) can be used to define characters and strings, respectively, but they have different purposes.
Single quotes are used for characters, and double quotes are used for strings.





