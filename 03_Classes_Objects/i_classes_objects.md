## 1. Terminologies


#### Class:

* _Classes_ are blueprints for objects. For example, a `Student` class is the blueprint for making a `Student` object.

#### Object:
* _Objects_ are instances of classes; a student object is one actual `Student` that exists in memory.

#### Properties:
* _Properties_ are characteristics of classes, such as the name, age, and grade of a `Student`.

#### Methods:
* _Methods_, also called _member functions_, are the functionality of the class.
Methods are what you can "do" with the object. For example, you can `calculateAverage()` of a `Student`'s marks.

#### Interface:
* An _interface_ is a specification that a class can implement. For example, extracurricular activities are common to objects other than students, and these activities generally happen in similar ways for different objects. So you could have an interface called `StudentActivities` that defines a `participate()` method. The `Student` class could implement the `StudentActivities` interface to allow students to participate in various activities.

#### Packages:
* _Packages_ are a way to group related code to keep it organized, or to make a library of code. Once a package is created, you can use `import` to allow you to directly reference classes in that package. For example, you could have a package called `edu.school` that contains the `Student` class, `Marks` class, and `StudentIQ` class.



## 2. Create a class

creating a new package and a class with some `properties` and a `method`.


### Step 1: Create a package
`Packages` can help keep the source code organized.

In the Project pane, under the Hello Kotlin project, right-click on the `src > main > kotlin` folder.
Select `New > Package` and call it `com.a1schools`


### Step 2: Create a class with properties
Classes are defined with the keyword class, and class names by convention start with a capital letter.

Right-click on the `com.a1schools` or `com.myapp` package.
Select `New > Kotlin` File / Class.

Under Kind, select Class, and name the class Student. IntelliJ IDEA includes the package name in the file and creates an empty Student class.

Inside the Student class, define and initialize var properties for the `name`, `age`, `marks`, and `gradeYear`. Initialize the properties with default values.

```Kotlin
package com.a1schools

class Student {
    var name: String = ""
    var age: Int = 0
    var marks: Double = 0.0
    var gradeYear: Int = 0
}
```
1. The Student class is created inside the com.a1schools package.
2. The class has four properties:

name of type `String` initialized with an empty string.
age of type `Int` initialized with 0.
marks of type `Double` initialized with 0.0.
gradeYear of type `Int` initialized with 0.


The properties are defined using the `var` keyword, which means they are mutable (their values can be changed).
The properties are initialized with default values using the `=` operator.

### Step 3: Create a main() function

Incase if we did not created the Student class yet  
* 1. Right-click on the com.a1schools package.
* 2. Select New > Kotlin File / Class.

select File, and name the file Student.
IntelliJ IDEA creates a new file called Student.kt inside the com.a1schools package.
Inside the Student.kt file, see the code:

```kotlin
package com.a1schools

class Student {
    var name: String = ""
    var age: Int = 0
    var marks: Double = 0.0
    var gradeYear: Int = 0
}

fun createStudent() {
    val student = Student()
    println("Student created!")
}

fun main() {
    createStudent()
}
```

i. The Student class remains the same as before, with its properties defined.

ii. A new function called `createStudent()` is defined outside the Student class.

*  Inside the `createStudent()` function, an instance of the Student class is created using `Student()` and assigned to a variable called student.
*  The `println()` function is used to print the string `"Student created!"` to the console.


iii. The `main()` function is defined outside the Student class.

*  Inside the `main()` function, the `createStudent()` function is called.

### Step 4: Add a method

Add a method to the `Student` class that prints the student's properties, you can modify the code as follows:

```Kotlin
package com.a1schools

class Student {
    var name: String = ""
    var age: Int = 0
    var marks: Double = 0.0
    var gradeYear: Int = 0

    fun printStudentInfo() {
        println("Name: $name")
        println("Age: $age")
        println("Marks: $marks")
        println("Grade Year: $gradeYear")
    }
}

fun createStudent() {
    val student = Student()
    student.name = "John Doe"
    student.age = 18
    student.marks = 85.5
    student.gradeYear = 12

    student.printStudentInfo()
}

fun main() {
    createStudent()
}
```
1. Inside the Student class, a new method called `printStudentInfo()` is added.

    * The method uses `println()` statements to print the values of the student's properties (name, age, marks, and gradeYear).
    * The $ symbol is used for string interpolation, which allows you to directly include the values of variables or properties within the string.


2. Inside the `createStudent()` function:

    * After creating an instance of the `Student` class, the properties of the student are set with some example values.
    * The `printStudentInfo()` method is called on the student instance to print the student's information.

Run your program and observe the output.
```
Name: John Doe
Age: 18
Marks: 85.5
Grade Year: 12
```



## 3. Add class constructors

In this task, you will create a constructor for the `Student` class and work with its properties.

### Step 1: Create a Constructor

In this step, you will add a constructor to the Student class. Previously, every instance of Student was created with the same attributes, and you had to change the attributes after creation. It is simpler to create the object with the correct attributes from the start.

In some programming languages like Java, constructors are defined by creating a method with the same name as the class.
In Kotlin, you define the constructor directly in the class declaration by specifying the parameters inside parentheses. These parameters can include default values.


Update the `Student` class to include three `constructor` parameters with default values and assign them to the corresponding properties.

```Kotlin
package com.a1schools

class Student(var name: String = "", var age: Int = 0, var marks: Double = 0.0, var gradeYear: Int = 0) {
    fun printStudentInfo() {
        println("Name: $name")
        println("Age: $age")
        println("Marks: $marks")
        println("Grade Year: $gradeYear")
    }
}

fun createStudent() {
    val student1 = Student("John Doe", 18, 85.5, 12)
    student1.printStudentInfo()

    val student2 = Student("Jane Smith", 17)
    student2.printStudentInfo()

    val student3 = Student(name = "Alice Johnson", gradeYear = 11)
    student3.printStudentInfo()
}

fun main() {
    createStudent()
}
```

i. The Student class definition is modified to include constructor parameters directly within the class declaration.

*    The `constructor` parameters are defined inside parentheses after the class name: (var name: String = "", var age: Int = 0, var marks: Double = 0.0, var gradeYear: Int = 0).
*    Each parameter is declared with a default value using the `=` operator.
*    The `var` keyword is used to declare the parameters as properties of the class, so they can be accessed and modified directly.


ii. Inside the createStudent() function:

*    Three instances of the Student class are created using different variations of the constructor.
*    `student1` is created by providing values for all constructor parameters: Student("John Doe", 18, 85.5, 12).
*    `student2` is created by providing values only for the name and age parameters, using the default values for marks and gradeYear: Student("Jane Smith", 17)
*    `student3` is created by specifying the parameter names explicitly and providing values for name and gradeYear, using the default values for age and marks: Student(name = "Alice Johnson", gradeYear = 11).
*    The printStudentInfo() method is called on each student instance to print their information.

```
Name: John Doe
Age: 18
Marks: 85.5
Grade Year: 12
Name: Jane Smith
Age: 17
Marks: 0.0
Grade Year: 0
Name: Alice Johnson
Age: 0
Marks: 0.0
Grade Year: 11
```



### Step 2: Add init blocks
