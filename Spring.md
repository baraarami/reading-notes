# Spring
## Serving Web Content with Spring MVC
![](https://stackify.com/wp-content/uploads/2017/10/How_MVC_Works-793x397.png)

## Starting with Spring Initializr
- If you use Gradle, visit the Spring Initializr to generate a new project with the required dependencies (Spring Web, Thymeleaf, and Spring Boot DevTools).
## Create a Web Controller:
```
package com.example.servingwebcontent;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class GreetingController {

	@GetMapping("/greeting")
	public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
		model.addAttribute("name", name);
		return "greeting";
	}

}
```
>***The implementation of the method body relies on a view technology (in this case, Thymeleaf) to perform server-side rendering of the HTML***
```
<!DOCTYPE HTML>
<html xmlns:th="http://www.thymeleaf.org">
<head> 
    <title>Getting Started: Serving Web Content</title> 
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
    <p th:text="'Hello, ' + ${name} + '!'" />
</body>
</html>
```

## Spring Boot Devtools
- Enables hot swapping.
- Switches template engines to disable caching.
- Enables LiveReload to automatically refresh the browser.
- Other reasonable defaults based on development instead of production.
## Run the Application
```
package com.example.servingwebcontent;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ServingWebContentApplication {

    public static void main(String[] args) {
        SpringApplication.run(ServingWebContentApplication.class, args);
    }

}
```
## Add a Home Page
```
<!DOCTYPE HTML>
<html>
<head> 
    <title>Getting Started: Serving Web Content</title> 
    <meta http-equiv="Content-Type" content="text/html; charset=UTF-8" />
</head>
<body>
    <p>Get your greeting <a href="/greeting">here</a></p>
</body>
</html>
```



**Spring App Basics**
* Spring MVC 
 - What you need to build it:
   * Build an application that has a static home page and that will also accept HTTP GET requests at: http://localhost:8080/greeting
   * body of HTML that contains a greeting: “Hello, World!”
   * Customize the greeting with an optional name parameter in the query string, and the URL will look like this: http://localhost:8080/greeting?name=User
   * name parameter value overrides the default value of World and is reflected in the response by the content changing to “Hello, User!”
 - What you need: 15 minutes, text editor or IDE, JDK 1.8 or later, Gradle 4+, and import the code to IntelliJ or Spring Tool Suite.
 - How to complete this guide: start from scatch, clone this git clone https://github.com/spring-guides/gs-serving-web-content.git in to your terminal, cd into it, and create a web controller. 
 - Spring initializr - use this to generate a new project with the required dependencies (Spring Web, Thymeleaf, and Spring Boot DevTools). If you use Gradle, visit the Spring Initializr to generate a new project with the required dependencies.
 - You can manually initialize it by navigating to https://start.spring.io, choose Gradle or Maven, click Dependencies and select Spring Web, Thymeleaf, and Spring Boot DevTools, and finally click generate. Download the resulting zip file.
 - Create a Web Controller:
   * HTTP requests are handled by a controller, and is identified by @Controller annotation.
   * GreetingController - handles GET requests for /greeting by returning the name of a View
   *  View - is responsible for rendering the HTML content
   * @GetMapping annotation - ensures that HTTP GET requests to /greeting are mapped to the greeting() method 
   * @RequestParam - binds the value of the query string parameter name into the name parameter of the greeting() method
 - Spring Boot Devtools - enables hot swapping, switches template engines to disable caching, enables LiveReload to automatically refresh the browser, and other reasonable defaults based on development instead of production. 
 - Run the Application: 
  * @SpringBootApplication - a convenient annotation that adds up:
   - @Configuration - tags the class as a source of bean definitions for the application context.
   - @EnableAutoConfiguration - tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings.
   - @ComponentScan - tells Spring to look for other components, configurations, and services in the com/example package, letting it find the controllers.
  * main() method  - uses Spring Boot’s SpringApplication.run() method to launch an application
 - Build an executable JAR that contains all the necessary dependencies, classes, and resources and run that.
 - Test the app on http://localhost:8080/greeting, and provide a name query string parameter by visiting http://localhost:8080/greeting?name=User to see if the greeting changes or not.

## [Spring MVC and Thymeleaf](https://www.thymeleaf.org/doc/articles/springmvcaccessdata.html)

**Spring MVC and Thymeleaf**
* Spring MVC application contains:
  - @Controller classes - responsible for preparing a model map with data and selecting a view to be rendered
  - model map allows for the complete abstraction of the view technology, and in the case of Thymeleaf, it is transformed into a Thymeleaf context object that makes all the defined variables available to expressions executed in templates
  - Spring model attributes:
    * model attributes - Spring MVC calls the pieces of data that can be accessed during the execution of views 
    * context variables - Thymeleaf language version of model attributes
  - Request parameters
    * Request parameters - easily accessed in Thymeleaf views, and passed from the client to server
  - Session attributes 
    * Session attributes - can be accessed by using the session. prefix or using #session
  - ServletContext attributes 
    * ServletContext attributes - shared between requests and sessions, and to access ServletContext attributes in Thymeleaf you can use the #servletContext. prefix
  - Spring beans
    * Thymeleaf allows accessing beans registered at the Spring Application Context with the @beanName syntax

