
# testing

## testing categories

* Unit: Unit Tests
* Integration: Integration Tests
* Service: Test on service layer (SOAP, REST)
* Functional: tests that want to guarantee the operation against different business rules (happy path, sad path and alternative flows)
* Non-functional tests: performance, load, security, usability, etc...
* Acceptance: acceptance testing (testing focus on the user perspective)


## unit testing


## integration testing


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

