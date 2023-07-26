# Yummy
A food recipes App Built with Jetpack Compose . The app uses room for local caching to facilitate offline support and follows the MVVM Clean Architectural pattern

### 1.UI layer
The role of the UI layer (or presentation layer) is to display the application data on the screen. Whenever the data changes, either due to user interaction (such as pressing a button) or external input (such as a network response), the UI should update to reflect the changes.
The UI layer is made up of two things:

* UI elements that render the data on the screen. You build these elements using Views or Jetpack Compose functions.
* State holders (such as ViewModel classes) that hold data, expose it to the UI, and handle logic.

### 2.Data layer
The data layer of an app contains the business logic. The business logic is what gives value to your app—it's made of rules that determine how your app creates, stores, and changes data.
The data layer is made of repositories that each can contain zero to many data sources. You should create a repository class for each different type of data you handle in your app.

### 3.Domain Layer
The domain layer is an optional layer that sits between the UI and data layers.
The domain layer is responsible for encapsulating complex business logic, or simple business logic that is reused by multiple ViewModels. This layer is optional because not all apps will have these requirements. You should use it only when needed—for example, to handle complexity or favor reusability

## Leaks application will be used to fix memory leaks within the kotlin app

* In the mix of things as i was following arround tutorials 
i was able to link my application to google play service 
that allows a one-tap to buy a recipe from the app but it is still something am looking into 
considering we still have cat 2 which is a continuation of this.
It has been commented out because it someting that i am still working on but it is located in the mealsScreen.kt file


## Tech Stack
 - [Kotlin](https://kotlinlang.org/docs/reference/) - Kotlin is a cross-platform, statically typed, general-purpose programming language with type inference. Kotlin is designed to interoperate fully with Java, and the JVM version of Kotlin's standard library depends on the Java Class Library, but type inference allows its syntax to be more concise
 
 * [Jetpack Components:](https://developer.android.com/topic/architecture?gclid=Cj0KCQjw8O-VBhCpARIsACMvVLOH1satX45o9f4PMQ4Sxr7bG9myl6-KZL9nYda8PJsHV7m2uJL8bzgaAmqiEALw_wcB&gclsrc=aw.ds)
    * [Jetpack Compose](https://developer.android.com/jetpack/compose?gclid=Cj0KCQjwhqaVBhCxARIsAHK1tiMMwHsxQ8Z25jyEdtLha9erq11wROoEfL6RqpGMprgbDTNuMO3_Ri8aAu5EEALw_wcB&gclsrc=aw.ds) -  Android’s modern toolkit for building native UI. It simplifies and accelerates UI development on Android
    * [View Model](https://developer.android.com/topic/libraries/architecture/viewmodel)-  store and manage UI-related data in a lifecycle conscious way.
    * [Lifecycle]( https://developer.android.com/topic/libraries/architecture/lifecycle) - Perform actions in response to a change in the lifecycle status of another component, such as activities and fragments.
    * [LiveData](https://developer.android.com/topic/libraries/architecture/livedata.html) - A lifecycle-aware data holder with the observer pattern
    * [Android KTX](https://developer.android.com/kotlin/ktx.html) - Android KTX is a set of Kotlin extensions that are included with Android Jetpack and other Android libraries. KTX extensions provide concise, idiomatic Kotlin to Jetpack, Android platform, and other APIs.
    * [AndroidX](https://developer.android.com/jetpack/androidx) - Major improvement to the original Android [Support Library](https://developer.android.com/topic/libraries/support-library/index), which is no longer maintained.

- [Retrofit](https://github.com/square/retrofit)- is a type-safe REST client for Android, Java and Kotlin, built as a powerful framework for consuming APIs

* [Dagger-Hilt](https://dagger.dev/hilt/)- a dependency injection library for Android that reduces the boilerplate of doing manual dependency injection in your project

* [Room](https://developer.android.com/topic/libraries/architecture/room.html) -  a persistence library provides an abstraction layer over SQLite for cache

* [Coroutines](https://developer.android.com/kotlin/coroutines) - a concurrency design pattern that you can use on Android to simplify code that executes asynchronously
* [Flow](https://developer.android.com/kotlin/flow)- In coroutines, a flow is a type that can emit multiple values sequentially, as opposed to suspend functions that return only a single value.
* [Ramcosta Navigation Library](https://composedestinations.rafaelcosta.xyz/) - A KSP library that processes annotations and generates code that uses Official Jetpack Compose Navigation under the hood. It hides the complex, non-type-safe and boilerplate code you would have to write otherwise.
* [CI/CD](https://codemagic.io/android-continuous-integration/) - Continuous integration systems let you automatically build and test your app every time you check in updates to your source control system. 

* [Coil](https://coil-kt.github.io/coil/compose/) - Image Loader library.

* [Accompanist-SwipeRefresh](https://google.github.io/accompanist/swiperefresh/) - A library which provides a layout which provides the swipe-to-refresh UX pattern, similar to Android's SwipeRefreshLayout.

## Data Source
This application fetches its data from the [The Meal Db](https://www.themealdb.com/api.php). Find the Documentation by following this [link](https://www.themealdb.com/api.php).

  ```
Part 2:
What is Room ?

The room persistence library it is an abstraction layer over SQLite.

The room is an ORM ( Object Relational Mapper ) for SQLite database in Android. It is part of the Architecture Components.

The room makes using SQLite much easier for you by implementing annotations.

Why use Room ?

. Compile Time Verification

In SQLite database if query has any error then it will cause Run-time exception. If we use Room then it will check the query at compile time itself. So that we can prevent the app from Run- time exception.

. Boilerplate Code

To convert the data from SQLite to DTO ( Data Transfer Object ) we need to write lot of codes. Those are internally managed by ROOM. So we don’t need to write the convertion code.

.Easily integrated with other Architecture components

Room is an Android Architecture component. So it can provide the data as observable like LiveData or RxJava’s Single object directly.

There are 3 main components are there in Room database.

1. Database
2. Dao
3. Entity

Entity

Represents a table within the database. Room creates a table for each class that has entity annotation, the fields in the class correspond to columns in the table. Therefore, the entity classes tend to be small model classes that don’t contain any logic.

Some useful annotations and their attributes :
— Foreign keys : names of foreign keys

— Indices : list of indicates on the table

— Primary keys : names of entity primary keys

— table name

Primary Key as its name indicates, this annotation points the primary key of the entity.autoGenerate — if set to true, then sqlite will be generating a unique id for the column

!! PrimaryKey(autoGenerate = true )

ColumnInfo allows specifying custom information about column

!!ColumnInfo(name = “column_name”)

Ignore field will not be persisted by Room

Embeded nested fields can be referenced directly in the SQL queries.

Database

To create a database in Room, we need to create an class and annotate it with database. To create the database we need to give what are all the tables should be there in this db and db version in the annotation.

Dao

To access database content we need to create data access object using an interface with Dao annotation. Inside this interface we need to create the methods required for db operations.

Here we can user 4 annotation :

Query
Insert
Update
Delete

Query to run raw query we need to user this annotation. Inside we need to pass the query.

1. Insert the data into database

2. Update the data into database

3. Delete the record from Database

Why Room Database over SQLite Database ?

Compile — time verification of Sql queries, so there is no more syntax errors at run time.
Very less code to write.
Support to integrate with other Architecture components.

The DB Base Url link is in the Constants.kt in the common-main-java directory
