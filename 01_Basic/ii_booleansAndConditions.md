## Boolean and Conditions

```kotlin
// Define some variables
val x = 5
val y = 10
val z = 15

// Check if both x and y are positive
if (x > 0 && y > 0) {
    println("Both x and y are positive.")
}

// Check if both x and z are positive
if (x > 0 && z > 0) {
    // This block won't be executed because z is not positive
    println("Both x and z are positive.")
}

```

In the first if statement, both x and y are greater than 0, so the condition x > 0 && y > 0 evaluates to true, and the message "Both x and y are positive." will be printed.

In the second if statement, although x is greater than 0, z is not. Therefore, the condition x > 0 && z > 0 evaluates to false, and the message will not be printed.

