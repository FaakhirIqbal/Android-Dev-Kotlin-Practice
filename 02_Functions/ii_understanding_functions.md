## More about Kotlin functions

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
