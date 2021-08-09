# Read: 13 - Related Resources and Integration Testing

# Related Resources and Integration Testing
## how to work with relationships between entities in Spring Data REST
## **One-to-One Relationship**
- Let's suppose we are building a user management system, and our boss asks us to store a mailing address for each user. A user will have one mailing address, and a mailing address will have only one user tied to it.
- This is an example of a one-to-one relationship, in this case between user and address entities.
- **Example :**
```
@OneToOne
    @JoinColumn(name = "address_id")
    @RestResource(path = "libraryAddress", rel="address")
    private Address address;

```
- Creating the Associations
   - This is done using the HTTP method PUT, which supports a media type of text/uri-list, and a body containing the URI of the resource to bind to the association.
   - **Example :**
   ```
   curl -i -X PUT -d "http://localhost:8080/addresses/1" 
    -H "Content-Type:text/uri-list" http://localhost:8080/libraries/1/libraryAddress
   ```
## **One-to-Many Relationship**
- **Example :**
>
>

```
public class Library {

    @OneToMany(mappedBy = "library")
    private List<Book> books;

}
```
## **Many-to-Many Relationship**
- A many-to-many relationship is defined using @ManyToMany annotation, to which we can add @RestResource.
```
public class Book {
    @ManyToMany(mappedBy = "books")
    private List<Author> authors;

}
```
# 
# Integration Testing in Spring
- The integration testing role in the application development cycle is verifying the end-to-end behavior of a system.
## Spring MVC Test Configuration
- **Enable Spring in Tests with JUnit 5**
>
>
```
@ExtendWith(SpringExtension.class)
@ContextConfiguration(classes = { ApplicationConfig.class })
@WebAppConfiguration
public class GreetControllerIntegrationTest {
    ....
}
```

- **Verify Test Configuration**
>
>
```
@Test
public void givenWac_whenServletContext_thenItProvidesGreetController() {
    ServletContext servletContext = webApplicationContext.getServletContext();
    
    Assert.assertNotNull(servletContext);
    Assert.assertTrue(servletContext instanceof MockServletContext);
    Assert.assertNotNull(webApplicationContext.getBean("greetController"));
}
```
- **Writing Integration Tests**
>
>
```
@Test
public void givenHomePageURI_whenMockMVC_thenReturnsIndexJSPViewName() {
    this.mockMvc.perform(get("/homePage")).andDo(print())
      .andExpect(view().name("index"));
}
```
#
## MockMvc Limitations

- it does use a subclass of the DispatcherServlet to handle test requests. 

- The MockMvc class wraps this TestDispatcherServlet internally. So, every time we send a request using the perform() method, MockMvc will use the underlying TestDispatcherServlet directly. 

- because Spring prepares a fake web application context to mock the HTTP requests and responses, it may not support all features of a full-blown Spring application.
![](https://res.infoq.com/presentations/spring-mvc-test-htmlunit/en/slides/sl9.jpg)


## [Related data in Spring (focus on the relationship annotations, not the curl requests)](https://www.baeldung.com/spring-data-rest-relationships)
**Working with Relationships in Spring Data REST**
  * One-to-One Relationship
    - Two entity classes can have a one to one relationship using the @OneToOne annotation, and the association will be owned by the first entity class by the end of the association.
    - @RestResource annotation is optional and can be used to customize the endpoint.
    - Make sure to have different names for each association resource.
    - To expose these entities as resources, create two repository interfaces for each of them, by extending the CrudRepository interface.
    - To create the resources add an instance, and have the API return the JSON object. Next send a GET request to the endpoint, which will return an empty object. Create the association using the HTTP method PUT and a body containing the URI of the resource to bind to the association. If you need to remove an association, we can call the endpoint with DELETE method.
  * One-to-Many Relationship
    - One-to-many relationship - defined using the @OneToMany and @ManyToOne annotations and can have the optional @RestResource annotation to customize the association resource
  * Many-to-Many Relationship
    - Many-to-many relationship - defined using @ManyToMany annotation, to which we can add @RestResource.
  * Testing the Endpoints With TestRestTemplate
    - Create a test class that injects a TestRestTemplate instance and defines the constants we will use.
    - Testing the One-to-One Relationship - create a @Test method that saves objects by making POST requests to the collection resources. Then save the relationship with a PUT request to the association resource and verifies that it has been established with a GET request to the same resource.
    - Testing the One-to-Many Relationship - create a @Test method that saves a instance and two other instances, send a PUT request to each object's association resource, and verify that the relationship has been saved.
    - Testing the Many-to-Many Relationship - create a test method that saves one record and two other records. Then it sends a PUT request to the association resource with the two URIs and verifies that the relationship has been established.


## [Baeldung: Spring Integration Testing](https://www.baeldung.com/integration-testing-in-spring)
**Integration Testing in Spring**
  * Integration testing plays an important role in the application development cycle by verifying the end-to-end behavior of a system.
  * Maven dependencies are required for running the integration tests: junit-jupiter-engine, junit-jupiter-api, and Spring test dependencies 
  * To assert results use Hamcrest and JSON path
  * Spring MVC Test Configuration - JUnit 5 enables the extension by adding the @ExtendWith annotation to our test classes and specifying the extension class to load, and to run the Spring test use SpringExtension.class. Also need the @ContextConfiguration annotation to load the context configuration and bootstrap the context that our test will use. Annotate the test with @WebAppConfiguration, which will load the web application context.
  * WebApplicationContext - provides a web application configuration, and it loads all the application beans and controllers into the context.
  * MockMvc - provides support for Spring MVC testing, and it encapsulates all web application beans and makes them available for testing. Initialize the mockMvc object in the @BeforeEach annotated method so that we don't have to initialize it inside every test.
  * Writing Integration Tests
    - First verify view name, and then verify response body.  
    - Send GET request with path variable and a query parameters, and finally send a POST request.
  * MockMvc Limitations 
    - MockMvc provides an elegant and easy-to-use API to call web endpoints and to inspect and assert their response at the same time, but has limitations.
    -  It uses a subclass of the DispatcherServlet to handle test requests, which is responsible for calling controllers and performing all of the familiar Spring magic. The MockMvc class wraps this TestDispatcherServlet internally, so every time we send a request using the perform() method, MockMvc will use the underlying TestDispatcherServlet directly. Therefore, there are no real network connections made, and won't test the whole network stack.
    - Spring prepares a fake web application context to mock the HTTP requests and responses, it may not support all features of a full-blown Spring application.
    
