# Accessing Data with JPA

## Define a Simple Entity

* `@Entity` indicating that it is a JPA entity
* `@GeneratedValue` to indicate that the value should be generated automatically.

## Create Simple Queries

* Spring Data JPA focuses on using JPA to store data in a relational database

* Its most compelling feature is the ability to create repository implementations automatically, at runtime, from a repository interface.

* Spring Data JPA also lets you define other query methods by declaring their method signature

* Spring Data JPA creates an implementation when you run the application.

## Create an Application Class

* Spring Initializr creates a simple class for the application

* `@SpringBootApplication` is a convenience annotation that adds all of the following:
    * `@Configuration`
    * `@EnableAutoConfiguration`
    * `@ComponentScan`

## Build an executable JAR

* If you use Gradle, you can run the application by using `./gradlew bootRun`.

* you can build the JAR file by using `./gradlew build`

# CrudRepository, JpaRepository, and PagingAndSortingRepository in Spring Data

* Spring Data repository interfaces has different kinds:


## CrudRepository

* the typical CRUD functionality:
    * save(…) – save an Iterable of entities. Here, we can pass multiple objects to save them in a batch
    * findOne(…) – get a single entity based on passed primary key value
    * findAll() – get an Iterable of all available entities in database
    * count() – return the count of total entities in a table
    * delete(…) – delete an entity based on the passed object
    * exists(…) – verify if an entity exists based on the passed primary key value

## PagingAndSortingRepository

* extends CrudRepository
* This interface provides a method findAll(Pageable pageable)
* using Pageable, we create a Pageable object with certain properties and we've to specify at least:
    * Page size
    * Current page number
    * Sorting
* Passing the pageable object to the Spring data query will return the results in question (the first parameter of PageRequest is zero-based)


## JpaRepository

* extends PagingAndSortingRepository which means it has all methods present in the CrudRepository as well.
