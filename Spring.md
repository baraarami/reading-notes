
# Spring

Spring MVC calls the pieces of data that can be accessed during the execution of views model attributes. The equivalent term in Thymeleaf language is context variables.

In Thymeleaf, these model attributes (or context variables in Thymeleaf jargon) can be accessed with the following syntax: ${attributeName}, where attributeName in our case is messages. This is a Spring EL expression. In short, Spring EL (Spring Expression Language) is a language that supports querying and manipulating an object graph at runtime.


# Request parameters
Request parameters are passed from the client to server and can be easily accessed in Thymeleaf views
 
 
 # ServletContext attributes
The ServletContext attributes are shared between requests and sessions. In order to access ServletContext attributes in Thymeleaf you can use the #servletContext. prefix


# Spring beans
Thymeleaf allows accessing beans registered at the Spring Application Context with the @beanName syntax

# Thymeleaf offers a set of Spring integrations that allow you to use it as a fully-featured substitute for JSP in Spring MVC applications.

These integrations will allow you to:

1. Make the mapped methods in your Spring MVC @Controller objects forward to templates managed by Thymeleaf, exactly like you do with JSPs.

2. Use Spring Expression Language (Spring EL) instead of OGNL in your templates.

3. Create forms in your templates that are completely integrated with your form-backing beans and result bindings, including the use of property editors, conversion services and validation error handling.

4. Display internationalization messages from message files managed by Spring (through the usual MessageSource objects).

5. Resolve your templates using Spring’s own resource resolution mechanisms.


![spring](https://user-images.githubusercontent.com/79080942/125173545-9c7bcd00-e1c8-11eb-96ad-43f48c859d27.JPG)

