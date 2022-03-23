# Related Resources and Integration Testing

* how to work with relationships between entities in Spring Data REST

### One-to-One Relationship

* defined using `@OneToOne annotation`
* to avoid `JsonMappingException`, We must be careful to have different names for each association resource
* example: a library has one address
* to expose these entities as resources, create two repository interfaces for each of them, by extending the CrudRepository interface
* add an instance from class to work with 
* Before creating an association, sending a GET request to this endpoint will return an empty object.
* The result of the POST request is a JSON object 
* After persisting both instances, we can establish the relationship by using one of the association resources
    * This is done using the HTTP method PUT
* To remove an association, we can call the endpoint with DELETE method


### One-to-Many Relationship

*  is defined using the `@OneToMany` and `@ManyToOne` annotations 
* example: adding a book to a library : library can have many books, and book is  elated to one library
* Let's associate the book with the library by sending a PUT request 
* We can verify the books in the library by using GET method 
* The result of the POST request is a JSON object 
* To remove an association, we can call the endpoint with DELETE method


### Many-to-Many Relationship

* is defined using `@ManyToMany` annotation
* example: an Author can has many books and book can has many authors
* To verify both books have been associated with the author, we can send a GET request
* To remove an association, we can call the endpoint with DELETE method

### Testing the Relationships

##### Testing the One-to-One Relationship

* create a @Test method that saves Library and Address objects by making POST requests 
* Then it saves the relationship with a PUT request to the resource and verifies that it has been established with a GET request

##### Testing the One-to-Many Relationship

* create a @Test method that saves a Library instance
* send a PUT request to each object's association resource, and verify that the relationship has been saved.

##### Testing the Many-to-Many Relationship

* create a test method that saves one record from one class  and two records from other class 
* Then it sends a PUT request to the association resource with the two URIs and verifies that the relationship has been established.

# Integration Testing in Spring

* several Maven dependencies needed for running the integration tests:  
    * junit-jupiter-engine
    * junit-jupiter-api
    * Spring test 
    *  Hamcrest 
    * JSON path

* how to configure and run the Spring enabled tests?
    
    * JUnit 5 defines an extension interface through which classes can integrate with the JUnit test.
    * We can enable this extension by adding the `@ExtendWith` annotation to our test classes and specifying the extension class to load.
    * To run the Spring test, we use `SpringExtension.class`
    * `@ContextConfiguration annotation` needed to load the context configuration and bootstrap the context that our test will use.
    * annotate the test with `@WebAppConfiguration`, which will load the web application context.

##### The WebApplicationContext Object

* provides a web application configuration
* It loads all the application beans and controllers into the context.

>@Autowired
>
>private WebApplicationContext webApplicationContext;

##### Mocking Web Context Beans

* support for Spring MVC testing
* It encapsulates all web application beans and makes them available for testing.
* initialize the mockMvc object in the @BeforeEach annotated method

##### Verify Test Configuration

* check that the right servletContext is being attached
* checking that a GreetController.java bean exists in the web context

##### Writing Integration Tests
* look at how to send requests with path variables and parameters
* assert that the proper view name is resolved, or that the response body is as expected

##### Verify Response Body
* andExpect(MockMvcResultMatchers.status().isOk()) will verify that response HTTP status is Ok (200).
* andExpect(MockMvcResultMatchers.jsonPath(“$.message”).value(“Hello World!!!”)) will verify that the response content matches with the argument
* andReturn() will return the MvcResult object, which is used when we have to verify something that isn't directly achievable

##### Send GET Request With Path Variable
* `MockMvcRequestBuilders.get(“/greetWithPathVariable/{name}”`, “John”) will send a request as `“/greetWithPathVariable/John“`.


##### Send GET Request With Query Parameters
* invoke `/greetWithQueryVariable?name={name}` endpoint from our test 
* `param(“name”, “John Doe”)` will append the query parameter in the GET request. This is similar to `“/greetWithQueryVariable?name=John%20Doe.“`

##### Send POST Request
* `MockMvcRequestBuilders.post(“/greetWithPost”)` will send the POST request
*  We can set path variables and query parameters in a similar way,  form data can be set only by param() method, similar to query parameters