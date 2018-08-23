
# testing (java specific)

## testing categories

* Unit: Unit Tests
* Integration: Integration Tests
* Service: Test on service layer (SOAP, REST)
* Functional: tests that want to guarantee the operation against different business rules (happy path, sad path and alternative flows)
* Non-functional tests: performance, load, security, usability, etc...
* Acceptance: acceptance testing (testing focus on the user perspective)

https://www.javaworld.com/article/2945040/testing-debugging/are-you-over-testing-your-software.html


Adam Bien - A Note On Java EE Testing  
https://youtu.be/x4Fxur-0SB0


## unit testing

Unit tests to be non-JavaEE-container based


How just about everyone gets unit testing wrong
There's a sweet spot with unit testing -- and most dev teams are missing it 
https://www.javaworld.com/article/2892225/testing-debugging/how-just-about-everyone-gets-unit-testing-wrong.html



## integration testing

Integration tests to use a JavaEE-container, but the test code itself should not be container dependent;


https://zeroturnaround.com/rebellabs/the-correct-way-to-use-integration-tests-in-your-build-process/
The correct way to use integration tests in your build process
* defines unit tests vs integration tests


https://antoniogoncalves.org/2012/10/24/no-you-dont-need-to-mock-your-soap-web-service-to-test-it/
No, you don’t need to mock your SOAP Web Service to test it
* mentions "integration testing with Arquillian"
* example of "Endpoint.publish()"
* test your SOAP Web Service inside the container and write an the integration test, using an in-memory web container. 


https://semaphoreci.com/community/tutorials/restful-integration-testing-with-wiremock-in-java
RESTful Integration Testing with WireMock in Java
* using WireMock as a mocking library
* using Dropwizard



https://paluch.biz/blog/53-unit-testing-of-web-services-with-junit-soap-services.html
Unit-Testing of Web-Services with JUnit - SOAP Services
* create a real SOAP Endpoint and uses remoting to access the WSDL and to invoke the service. 
* example of "Endpoint.publish()"


http://www.oracle.com/technetwork/articles/java/integrationtesting-487452.html
Integration Testing for Java EE. By Adam Bien
* Arquillian - an open source testing framework integrated as a JUnit TestRunner.
* Arquillian consists of a runner and container part.
* You have a full control over which classes are deployed and injected.
* Testing everything inside an embedded container is convenient but unproductive.
* Using an embedded container to test your business logic is not only unproductive, but it is also conceptually wrong. Unit tests should validate your business logic, not the container behavior.
* Only a fraction of all integration tests can be beneficially implemented with embeddable containers or test frameworks such as Arquillian. Although such tests represents only a fraction of the overall integration test base, these tests represent the ultimate killer use cases. Without an embeddable container, it is impossible to test infrastructure-dependent business logic without changing the integration environment or polluting the production code with test helpers.


http://nigel-eke.com/unit-integration-testing-rest-services/
Unit & Integration Testing REST Services



https://blog.codecentric.de/2016/06/spring-boot-apache-cxf-soap-webservices-testen/


## non-functional tests: performance

* minimise api response times
* minimise page/screen load times


## non-functional tests: load

* dev and test environments tend not to have production data volumes, and they tend to be downsized (less storage space, less memory)
* test against an anonymised copy of production data, if possible, else if it does not yet exist, production-equivalent data could be randomly generated.


## non-functional tests: security

* prevent unauthorised access.
* ensure authorised users only have access to permitted data and functionality.


## non-functional tests: usability

https://en.wikipedia.org/wiki/Usability_testing

https://en.wikipedia.org/wiki/Don%27t_Make_Me_Think

https://www.usability.gov/how-to-and-tools/methods/usability-testing.html

https://uxplanet.org/why-is-it-important-to-do-usability-testing-5080a5640df3

accessibility testing is a subset of usability testing. it is performed to ensure that the application being tested is usable by people with disabilities like hearing, color blindness, old age and other disadvantaged groups.

https://www.w3.org/wiki/Accessibility_testing

https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA

https://www.gov.uk/service-manual/technology/testing-for-accessibility

https://accessibility.blog.gov.uk/2017/02/24/what-we-found-when-we-tested-tools-on-the-worlds-least-accessible-webpage/

http://www.karlgroves.com/2013/09/05/the-6-simplest-web-accessibility-tests-anyone-can-do/

