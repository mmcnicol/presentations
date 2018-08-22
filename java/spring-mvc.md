# spring mvc


## controller


URI variables can be declared at the class and method level:

```java
@Controller
@RequestMapping("/owners/{ownerId}")
public class OwnerController {

    @GetMapping("/pets/{petId}")
    public Pet findPet(@PathVariable Long ownerId, @PathVariable Long petId) {
        // ...
    }
}
```

```java
@GetMapping(path = "/pets/{petId}", produces = "application/json;charset=UTF-8")
@ResponseBody
public Pet getPet(@PathVariable String petId) {
    // ...
}
```


http://localhost:8080/greeting?name=User

```java
@GetMapping("/greeting")
public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
    model.addAttribute("name", name);
    return "greeting";
}
```

You can narrow request mappings based on request parameter conditions. You can test for the presence of a request parameter ("myParam"), for the absence ("!myParam"), or for a specific value ("myParam=myValue"):

```java
@GetMapping(path = "/pets/{petId}", params = "myParam=myValue")
public void findPet(@PathVariable String petId) {
    // ...
}
```

```java
@PostMapping(path = "/pets", consumes = "application/json")
public void addPet(@RequestBody Pet pet) {
    // ...
}
```

* [spring guide serving-web-content](https://spring.io/guides/gs/serving-web-content/)


## session management

use session.setAttribute() and session.getAttribute()
e.g. session.setAttribute("user", user);

* [httpsession-management-in-springmvc](https://stackoverflow.com/questions/17145526/httpsession-management-in-springmvc)
* [spring-mvc-session-tutorial](https://www.javacodegeeks.com/2013/04/spring-mvc-session-tutorial.html)


## security

* [spring guide; Securing a Web Application](https://spring.io/guides/gs/securing-web/)


## form submission

* [spring guide; handling-form-submission](https://spring.io/guides/gs/handling-form-submission/)


## validate form input

* [spring guide; validating-form-input](https://spring.io/guides/gs/validating-form-input/)


## unit testing and integration testing

* [spring guide; Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot/)


## template engines

* [mustache](http://mustache.github.io/mustache.5.html)
* [the-joy-of-mustache-server-side-templates-for-the-jvm](https://spring.io/blog/2016/11/21/the-joy-of-mustache-server-side-templates-for-the-jvm)


## links
* [SPRING INITIALIZR](https://start.spring.io/)
* [spring guides](https://spring.io/guides)
* [Spring Framework Documentation](https://docs.spring.io/spring/docs/5.0.8.RELEASE/spring-framework-reference/index.html)
* [spring blog](https://spring.io/blog/)
