# Spring

* this notes will walks you through the process of creating a “Hello, World” web site with Spring

* You will build an application that has a static home page and that will also accept HTTP GET requests at: http://localhost:8080/greeting.

* It will respond with a web page that displays HTML. The body of the HTML will contain a greeting: “Hello, World!”

* What You Need: About 15 minutes, A favorite text editor or IDE, JDK 1.8 or later, Gradle 4+ or Maven 3.2+, Spring Tool Suite (STS), IntelliJ IDEA


#### Starting with Spring Initializr
 
 * Navigate to https://start.spring.io and do installations

 * Choose either Gradle or Maven and the language you want to use

 * Click Dependencies and select Spring Web, Thymeleaf, and Spring Boot DevTools then generate

 * Download the resulting ZIP file

 #### Download the resulting ZIP file

 * To speed up this refresh cycle, Spring Boot offers with a handy module known as spring-boot-devtools:

    * Enables hot swapping.

    * Switches template engines to disable caching.

    * Enables LiveReload to automatically refresh the browser.

    * Other reasonable defaults based on development instead of production.

    #### Create a Web Controller

    * In Spring’s approach to building web sites, HTTP requests are handled by a controller

    * You can identify the controller by the @Controller annotation.
    * A View is responsible for rendering the HTML content. 

#### Run the Application

The following listing (from src/main/java/com/example/servingwebcontent/ServingWebContentApplication.java) shows the application class:

package com.example.servingwebcontent;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

>@SpringBootApplication
>
>public class ServingWebContentApplication {
>
>    public static void main(String[] args) {
>
>        SpringApplication.run(ServingWebContentApplication.class, args);
>
>    }
>
>}

* @SpringBootApplication is a convenience annotation that adds all of the following:

    * @Configuration
    * @EnableAutoConfiguration
    * @ComponentScan

* The main() method uses Spring Boot’s SpringApplication.run() method to launch an application.

#### Build an executable JAR

* You can run the application from the command line with Gradle or Maven

> java -jar build/libs/gs-serving-web-content-0.1.0.jar

>java -jar target/gs-serving-web-content-0.1.0.jar

#### Test the Application

* Now that the web site is running, visit http://localhost:8080/greeting, where you should see “Hello, World!”


## pring MVC and Thymeleaf: how to access data from templates

* Spring MVC application, @Controller classes are responsible for preparing a model map with data and selecting a view to be rendered


#### Spring model attributes

* Add attribute to Model via its addAttribute method:

> @RequestMapping(value = "message", method = RequestMethod.GET)
>
>        public String messages(Model model) {
>
>            model.addAttribute("messages", messageRepository.findAll());
>
>            return "message/list";
>
>        }

* Return ModelAndView with model attributes included:

>@RequestMapping(value = "message", method = RequestMethod.GET)
>
>        public ModelAndView messages() {
>
>            ModelAndView mav = new ModelAndView("message/list");
>
>            mav.addObject("messages", messageRepository.findAll());
>
>            return mav;
>        }

* Expose common attributes via methods annotated with @ModelAttribute:

>@ModelAttribute("messages")
>
>        public List<Message> messages() {
>
>            return messageRepository.findAll();
>
>        }


#### Request parameters

* Request parameters can be easily accessed in Thymeleaf views. Request parameters are passed from the client to server

#### Session attributes

* dd mySessionAttribute

#### ServletContext attributes

* The ServletContext attributes are shared between requests and sessions. In order to access ServletContext attributes in Thymeleaf you can use the #servletContext.


#### Spring beans

* Thymeleaf allows accessing beans registered at the Spring Application Context with the @beanName


