# Spring Boot and OAuth2
* simple: a very basic static app with just a home page and unconditional login
* click: adds an explicit link that the user has to click to login.
* logout: adds a logout link 
* two-providers: adds a second login provider
* custom-error: adds an error message for unauthenticated users

# Single Sign On With GitHub
##### Creating a New Project
* create a Spring Boot application then import that project into your favorite IDE
##### Add a Home Page
*  create index.html, add CSS file to style, and javascript
* add  webjars "locator" which is provided as a library by the webjars site

##### Securing the Application with GitHub and Spring Security
* add Spring Security as a dependency
* configure your app to use GitHub as the authentication provider, by : Add a New GitHub app, Configure application.yml, Boot up the application

##### Add a New GitHub App
* Select "New OAuth App" and then the "Register a new OAuth application" page is presented
* Enter an app name and description. Then, enter your app’s home page,  indicate the Authorization callback URL , click Register Application.

##### Configure `application.yml`
* to make the link to GitHub, add the following to your `application.yml`

##### Boot Up the Application
* you can run your app again and visit the home page at `http://localhost:8080`, but  you should be redirected to login with GitHub
* If you stay logged in to GitHub, you won’t have to re-authenticate with this local app, even if you open it in a fresh browser 
* It’s safe to grant access to this sample since only the app running locally can use the tokens and the scope it asks for is limited

##### Add a Welcome Page
* The `/user` Endpoint, use of `@RestController`, `@GetMapping`, and the `OAuth2User` injected into the handler method.

##### Making the Home Page Public
* To make the link visible, switch off the security on the home page by extending `WebSecurityConfigurerAdapter`
* You want to allow:

    * `/` since that’s the page you just made dynamic, with some of its content visible to unauthenticated users

    * `/error` a Spring Boot endpoint for displaying errors

    * `/webjars/**`  JavaScript will run for all visitors, authenticated or not

##### Add a Logout Button
* The logout() function does a POST to `/logout`
* Generating a 401 in the Server: declare a `@Bean` of type `OAuth2UserService`, it will be used to identify the user principal

