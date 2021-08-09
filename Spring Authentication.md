# Spring Authentication

###### Authentication (who are you?)
###### Authorization (what are you allowed to do?).


## Authentication and Access Control
- for independent problemslike ...
    - authentication (who are you?) 
    - authorization (what are you allowed to do?)...
-  has only one method: `AuthenticationManager`

```
public interface AuthenticationManager {

  Authentication authenticate(Authentication authentication)
    throws AuthenticationException;
}
```
- what can do ? 
- Return an Authentication `authenticated=true` >> input represents a valid principal.

- Throw >> input represents an invalid principal.

- Return `null`>> if it cannot decide.
- most commonly used implementation of `AuthenticationManager` is `ProviderManager`
- example: 
```
public interface AuthenticationProvider {

	Authentication authenticate(Authentication authentication)
			throws AuthenticationException;

	boolean supports(Class<?> authentication);
}
```
![](https://raw.githubusercontent.com/spring-guides/top-spring-security-architecture/master/images/authentication.png)
## Customizing Authentication Managers
 - The most commonly used helper is the `AuthenticationManagerBuilder`, which is great for :
     -  setting up in-memory
     -  JDBC
     - LDAP user details


# Web Security
![](https://raw.githubusercontent.com/spring-guides/top-spring-security-architecture/master/images/security-filters.png)

## Creating and Customizing Filter Chains
- The default fallback filter chain in a Spring Boot application (the one with the `/**` request matcher)has a predefined order of `SecurityProperties.BASIC_AUTH_ORDER`
- example :
```
@Configuration
@Order(SecurityProperties.BASIC_AUTH_ORDER - 10)
public class ApplicationConfigurerAdapter extends WebSecurityConfigurerAdapter {
  @Override
  protected void configure(HttpSecurity http) throws Exception {
    http.antMatcher("/match1/**")
     ...;
  }
}
```
# Spring Auth Cheat Sheet
- Step 1: set up a user model and repo
- Step 2: create a controller for that model
- Step 3: UserDetailsServiceImpl implements UserDetailsService
- Step 4: ApplicationUser implements UserDetails
- Step 5: WebSecurityConfig extends WebSecurityConfigurerAdapter
- Step 6: registration page
- Step 7: login page
- ***Resourses :***
- [Spring Security Architecture](https://spring.io/guides/topicals/spring-security-architecture/)





![](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/authentication.png)


 * Authentication and Access Control
   - Two problems of app security: authentication and authorization 
   - Authentication - main strategy interface for authentication is AuthenticationManager
     * AuthenticationManager can do one of 3 things in its authenticate() method: 
       - Return an Authentication if it can verify that the input represents a valid principal.
       - Throw an AuthenticationException if it believes that the input represents an invalid principal.
       - Return null if it cannot decide.
     * AuthenticationException is a runtime exception, and its usually handled by an application in a generic way, depending on the style or purpose of the application.
     * Customizing Authentication Managers
      - Spring Security provides some configuration helpers to quickly get common authentication manager features set up in your application, and the most common one is AuthenticationManagerBuilder.
      - AuthenticationManagerBuilder - or setting up in-memory, JDBC, or LDAP user details or for adding a custom UserDetailsService
    *  Authorization or Access Control
      - Authorization - core strategy here is to use the AccessDecisionManager. There are three implementations provided by the framework and all three delegate to a chain of AccessDecisionVoter instances.
      - AccessDecisionVoter considers an Authentication and a secure Object, which has ConfigAttributes.
  * Web Security
  ![](https://github.com/spring-guides/top-spring-security-architecture/raw/master/images/filters.png)
    - Spring Security in the web tier is based on Servlet Filters.
    - The typical layering of the handlers for a single HTTP request client sends a request to the application, and the container decides which filters and which servlet apply to it based on the path of the request URI.
    - Filters form a chain and the order of the chain are important, and a servlet can handle one request.
    - Filter can veto the rest of the chain if it wants to handle the request itself, and a filter can also modify the request or the response used in the downstream filters and servlet. 
    - Spring Boot manages the filter chain through two mechanisms: @Beans of type Filter can have an @Order or implement Ordered
    - Spring Security is installed as a single Filter in the chain, and its concrete type is FilterChainProxy. Inside of the single filter there are additional filters.
    - Another layer of indirection in the security filter, and its usually installed in the container as a DelegatingFilterProxy, which does not have to be a Spring @Bean. 
    - Can be multiple filter chains all managed by Spring Security in the same top level FilterChainProxy and all are unknown to the container. 
  * Creating and Customizing Filter Chains
    - default fallback filter chain in a Spring Boot application (the one with the /** request matcher) has a predefined order of SecurityProperties.BASIC_AUTH_ORDER
    - can switch it off completely by setting security.basic.enabled=false
    - or you can use it as a fallback and define other rules with a lower order by add a @Bean of type WebSecurityConfigurerAdapter or WebSecurityConfigurer and decorate the class with @Order 
  * Request Matching for Dispatch and Authorization 
    - Security filter chain has a request matcher that is used to decide whether to apply it to an HTTP request, once the decision is made to apply a particular filter chain, no others are applied. 
    - You can have more fine-grained control of authorization by setting additional matchers in the HttpSecurity
  * Combining Application Security Rules with Actuator Rules
    - Add the Actuator to a secure application, which adds an additional filter chain that applies only to the actuator endpoints. It is defined with a request matcher that matches only actuator endpoints and it has an order of ManagementServerProperties.BASIC_AUTH_ORDER.
  * Method Security
    - Spring Security offers support for applying access rules to Java method executions. For users the access rules are declared using the same format of ConfigAttribute strings, but in a different place in the code.
  * Working with Threads
    - Spring Security is thread-bound because it needs to make the current authenticated principal available to a wide variety of downstream consumers. 
    - Basic building block is the SecurityContext, which may contain an Authentication, and you can always access and manipulate the SecurityContext through static convenience methods in SecurityContextHolder, which manipulate a ThreadLocal.
  * Processing Secure Methods Asynchronously
    - SecurityContext is thread-bound, so if you want to do any background processing that calls secure methods, you need to ensure that the context is propagated. 
