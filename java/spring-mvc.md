# spring mvc


## controller

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


## for submission

* [spring guide; handling-form-submission](https://spring.io/guides/gs/handling-form-submission/)


## validate form input

* [spring guide; validating-form-input](https://spring.io/guides/gs/validating-form-input/)


## unit testing and integration testing

* [spring guide; Building an Application with Spring Boot](https://spring.io/guides/gs/spring-boot/)


## links
* [SPRING INITIALIZR](https://start.spring.io/)
* [spring guides](https://spring.io/guides)
