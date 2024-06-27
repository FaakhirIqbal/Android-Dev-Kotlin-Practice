## Visibility Modifiers

In Kotlin, visibility modifiers are used to control the accessibility and visibility of classes, objects, interfaces, constructors, functions, properties, and their setters. They determine from where and how these elements can be accessed within a program. Kotlin provides four visibility modifiers: `private`, `protected`, `internal`, and `public`.

### 1. private:
   - When an element is declared as `private`, it is only visible and accessible within the same class or source file where it is defined.
   - Private elements cannot be accessed from outside the class or source file, not even by subclasses or other classes in the same package.
   - Private visibility is the most restrictive and provides the highest level of encapsulation.

### 2. protected:
   - The `protected` modifier is similar to `private`, but with an additional feature.
   - Protected elements are visible and accessible within the same class and its subclasses.
   - However, protected elements are not accessible from outside the class hierarchy.
   - Subclasses can access and override protected members of their superclass.

### 3. internal:
   - The `internal` modifier is unique to Kotlin and is not available in languages like Java.
   - Internal elements are visible and accessible within the same module.
   - A module is a set of Kotlin files compiled together, such as a library, a client application, or a server application in an IntelliJ project.
   - Internal elements can be accessed from anywhere within the same module but are not accessible from outside the module.
   - This allows for a level of encapsulation and modularity within a project.

### 4. public (default):
   - If no visibility modifier is specified, the default visibility is `public`.
   - Public elements are visible and accessible from everywhere, both within and outside the class.
   - Classes, methods, properties, and member variables are `public` by default in Kotlin.
   - Public visibility provides the least restriction and allows the widest accessibility.

Regarding member variables (properties) within a class:
  - By default, properties are `public`, which means they can be accessed and modified from anywhere.
  - If a property is defined with `var`, it is mutable and can be both read and written.
  - If a property is defined with `val`, it is read-only and can only be assigned a value during initialization.

If you want to have a property that can be read and written within the class but only read from outside the class, you can declare the property and its getter as public and make the setter private. Here's an example:

```kotlin
class Student(
    private var name: String // private property
) {
    // Public getter and private setter for studentName
    var studentName: String
        get() = name // Public getter
        private set(value) { // Private setter
            name = value
        }

    // Method to change the name within the class
    fun updateName(newName: String) {
        studentName = newName
    }

    // Method to display student details
    fun displayDetails() {
        println("Student Name: $studentName")
    }
}

fun main() {
    // Creating an instance (object) of Student class
    val student = Student("John Doe")
    
    // Displaying initial student details
    student.displayDetails()
    
    // Trying to change the name directly from outside the class (will not work)
    // student.studentName = "Jane Doe" // Uncommenting this line will cause a compilation error

    // Changing the name using a method within the class
    student.updateName("Jane Doe")
    
    // Displaying updated student details
    student.displayDetails()
}

```

In this case, the `studentName` property is declared as `var`, so it can be read and written within the `Student` class. However, the setter is marked as `private`, which means the property can only be modified within the class. From outside the class, the `studentName` property can only be read but not modified directly.

Visibility modifiers provide a way to control the accessibility and encapsulation of code elements in Kotlin. They allow you to define the boundaries and restrict access to certain parts of your program, promoting better code organization, maintainability, and security.

