
# Android and Kotlin Notes

## Kotlin Basics

### Variables
- `val`: Equivalent to `const` (immutable).
- `var`: Mutable variable.

### Functions
- Syntax: `fun main(): ReturnType { /* code */ }`
- Default return type is `Unit`, equivalent to `void`.
- Parameters are immutable.

### Entry Point in Android
- `onCreate` function is the entry point and calls other functions to build the user interface.

### Functions as First-Class Constructs
- Functions can be treated as data types.
```kotlin
fun printHello() {
    print("Hello")
}
val callMe = ::printHello
callMe()
```
- `::` is a function reference operator.

### Lambda Expressions
- Store functions directly in a variable.
```kotlin
val trick = {
    println("No treat!")
}
val trickFunction = trick
trickFunction()
```
- The result of the last expression in the lambda is the return value.
- Trailing lambda syntax can be used when the function parameter is the last parameter.
- If a function expects a single parameter and no name is provided, Kotlin assigns it the name `it`.

### Higher-Order Functions
- Functions that take functions as arguments or return functions.
```kotlin
fun trickOrTreat(isTrick: Boolean, extraTreat: ((Int) -> String)?): () -> Unit {
    if (isTrick) {
        return trick
    } else {
        if (extraTreat != null) {
            println(extraTreat(5))
        }
        return treat
    }
}
val trick = {
    println("No treat!")
}
val treat: () -> Unit = {
    println("Have treat!")
}
```
- Kotlin library provides higher-order functions like `repeat`.

### Properties and Backing Fields
- Properties use a backing field to hold values in memory.
```kotlin
var speakerVolume = 2
    set(value) {
        field = value
    }
```

### Classes
- All classes are final by default.
- `data class`: Must have at least one parameter in the constructor, cannot be inherited, and provides getter, setter, and utility functions.
- `object`: Used to create a singleton class.
- `sealed class`: Used to maintain state of different types.

### Companion Objects
- Define a singleton object inside a class.
```kotlin
class MyClass {
    companion object {
        fun create(): MyClass = MyClass()
    }
}
```

### Scope Functions
- Allow you to access properties and methods of a class without referring to the object name.
- Examples: `let`, `run`, `apply`, `also`, `with`.

### Collections and Higher-Order Functions
- Types: `Array`, `List`, `Map`.
- Functions: `forEach`, `map`, `filter`, `groupBy`, `fold`, `sortedBy`.

### Coroutines
- `suspend` function: Can suspend without blocking.

### Reflection
- Allows developers to inspect, modify, and create new objects at runtime.
- Slower because it happens during runtime.
- Libraries: Gson (uses reflection), Moshi (uses annotation processor).

## Android Basics

### Core Components
- Activity
- Service
- Broadcast Receiver
- Content Provider

### Jetpack Compose
- Toolkit for building UI with composable functions.
- Composables are stateless by default.
- State hoisting: Moving state outside a composable so others can use it.
- Declarative UI framework.

### Testing
- Local Test: Tests small pieces of code without requiring an emulator or device.
- Instrumentation Test: Tests UI interactions.

### Android Manifest
- Describes essential information about your app.
- Intent filters.

### Layouts
- `View`: Basic building block for the user interface.
- `ViewGroup`: Subclass of `View`.

### App Architecture
- Separation of concerns.
- UI Layer and Data Layer.

### Room Database
- Components: `@Entity`, `@Dao`, `@Database`.
- Repository class abstracts access to multiple data sources.

### Context
- `getContext()`: Returns the context of the activity.
- `getApplicationContext()`: Returns the context of the application.

### WorkManager
- Schedules long-running tasks in the background.
- Allows scheduling tasks with constraints and chaining work requests.
- Main classes: `Worker`, `WorkRequest`.

### Dependency Injection
- Design pattern for giving objects their instance variables.
- Constructor injection is a type of dependency injection.

## Additional Topics
- Modularization
- Invariant, Covariant, Contravariant
- Generic types and covariance in Kotlin
- DiffUtils
- Remember and RememberSavable in Jetpack Compose



  
# Android Unit Testing Notes

## Unit Testing in Android

### Test Doubles
When testing functions that require external dependencies (e.g., HTTP requests), using the actual dependencies can be time-consuming and unreliable. Instead, we use test doubles, which are alternative implementations of these dependencies.

#### Types of Test Doubles
1. **Fake**: Functional substitution optimized for testing. It has working implementations but is simplified.
2. **Stub**: Returns predefined data. It is used to provide the necessary indirect input to the system under test.
3. **Mock**: Records interactions during the test. It is used to verify that certain interactions took place.

### Mockito
Mockito is a popular mocking framework for creating test doubles in Android. It allows you to create mocks, stubs, and spies to facilitate unit testing.

### Object vs Data Structure
- **Object**: Exposes behavior. not everything is object object is something which exposes behaviour   
- **Data Structure**: Exposes data. It is a collection of data without behavior.
- they should not be combined

### Structure of a Unit Test
1. **Arrange**: Set up the testing objects and prepare the prerequisites for your test.
2. **Act**: Execute the function or method being tested.
3. **Assert**: Verify that the action of the method under test behaves as expected.

### Test-Driven Development (TDD)
TDD is a software development process where you write tests before writing the actual code. The cycle typically follows these steps:
1. **Write a Test**: Write a test for the next bit of functionality you want to add.
2. **Run the Test**: Run the test and see it fail (since the functionality is not yet implemented).
3. **Write Code**: Write the minimum amount of code required to make the test pass.
4. **Run Tests**: Run all tests and see them pass.
5. **Refactor**: Refactor the code to improve its structure while ensuring that all tests still pass.

### Example of a Unit Test Structure

```kotlin
@Test
fun testFunction() {
    // Arrange
    val dependency = mock(Dependency::class.java)
    val classUnderTest = ClassUnderTest(dependency)
    `when`(dependency.someMethod()).thenReturn(someValue)

    // Act
    val result = classUnderTest.methodUnderTest()

    // Assert
    assertEquals(expectedValue, result)
    verify(dependency).someMethod()
}
```