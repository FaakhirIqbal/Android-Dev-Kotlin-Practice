## Boolean and Conditions

### 1. Compare conditions and booleans

```kotlin
val x = 5
val y = 10
val isEqual = x == y
val isGreater = x > y

println("Is Equal: $isEqual") // Output: Is Equal: false
println("Is Greater: $isGreater") // Output: Is Greater: false
```

### 2. booleans and boolean operators
```kotlin
val bool1 = true
val bool2 = false
val andResult = bool1 && bool2 // Logical AND
val orResult = bool1 || bool2 // Logical OR

println("AND Result: $andResult") // Output: AND Result: false
println("OR Result: $orResult") // Output: OR Result: true
```


### 3. Conditions if and else

```kotlin
val age = 25

if (age >= 18) {
    println("You are an adult")
} else {
    println("You are a minor")
}
```

### 4. Range operator in Kotlin ".."

```kotlin
val range = 1..5 // Represents the range from 1 to 5 inclusive

for (num in range) {
    println(num)
}
```

### 5. logical operator AND && and logical operator OR ||
```kotlin
val num1 = 10
val num2 = 20

if (num1 > 0 && num2 > 0) {
    println("Both numbers are positive")
} else {
    println("At least one number is not positive")
}
```

### 6. when statement
**when** is a keyword used to create a when expression, which is similar to a switch or case statement in other languages
```kotlin
val x = 5

when (x) {
    1 -> println("x is 1")
    2 -> println("x is 2")
    in 3..5 -> println("x is between 3 and 5") // Using range in when statement
    else -> println("x is neither 1 nor 2")
}

```
