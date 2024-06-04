## Pairs, triples, collections, constants, and extension functions


### 1. Pairs/Triples:
   - Pairs and triples are simple data structures that allow you to group two or three values together, respectively.

     ```kotlin
     val studentGrade = Pair("John", 85)
     val studentDetails = Triple("Alice", 20, listOf("Math", "Science"))
     println(studentGrade.first) // Output: John
     println(studentDetails.second) // Output: 20
     ```

### 2. Collections:
   - Collections are used to store and manipulate groups of objects. Kotlin provides various collection types like lists, sets, and maps.

     ```kotlin
     val studentActivities = listOf("Football", "Painting", "Debate")
     val uniqueActivities = setOf("Football", "Painting", "Debate", "Painting")
     val studentGrades = mapOf("John" to 85, "Alice" to 92, "Bob" to 78)
     println(studentActivities) // Output: [Football, Painting, Debate]
     println(uniqueActivities.size) // Output: 3
     println(studentGrades["Alice"]) // Output: 92
     ```

### 3. Constants:
   - Constants are used to define immutable values that do not change throughout the program.

     ```kotlin
     const val MAX_STUDENTS = 100
     const val MIN_GRADE = 60
     fun isEligibleForScholarship(grade: Int) = grade >= MIN_GRADE
     println(isEligibleForScholarship(85)) // Output: true
     ```

### 4. Extension Functions:
   - Extension functions allow you to add new functionality to existing classes without modifying their source code.

     ```kotlin
     fun List<String>.getTopActivities(limit: Int): List<String> {
         return this.distinct().take(limit)
     }
     val activities = listOf("Football", "Painting", "Debate", "Painting", "Chess")
     val topActivities = activities.getTopActivities(3)
     println(topActivities) // Output: [Football, Painting, Debate]
     ```

    We define an extension function `getTopActivities` on the `List<String>` class. It returns a list of the top `limit` distinct activities from the list.


#### Summary: pairs/triples, collections, constants, and extension functions can be used

- **Pairs** and triples can be used to group related information about a student, such as their name and grade or name, age, and list of subjects.
- **Collections** can be used to store and manipulate lists of student activities, unique activities, or student grades using different collection types like lists, sets, and maps.
- **Constants** can be used to define fixed values related to students, such as the maximum number of students allowed or the minimum grade required for eligibility.
- **Extension functions** can be used to add custom functionality to existing classes, such as retrieving the top activities from a list of student activities.

These concepts provide powerful tools for organizing and processing data related to students and their activities in Kotlin.
