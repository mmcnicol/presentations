
# devops - continuous testing


* the concept of continuous testing was originally proposed as a way of reducing waiting time for feedback to developers by introducing development environment-triggered tests as well as more traditional developer/tester-triggered tests
* continuous testing is the process of executing automated tests as part of the software delivery pipeline to obtain immediate feedback on the business risks associated with a software release candidate
* for continuous testing, the scope of testing extends from validating bottom-up requirements or user stories to assessing the system requirements associated with overarching business goals


## adoption drivers
* traditional testing processes/cycles are too slow. traditional methods of testing rely heavily on manual testing
* even after more automation is added to the existing test process, managers still lack adequate insight into the level of risk associated with an application at any given point in time
  * understanding these risks is critical for making the rapid go/no go decisions involved in continuous delivery processes
  * for the test results to accurately indicate whether each release candidate meets business expectations, the approach to designing tests must be based on the business's tolerance for risks related to security, performance, reliability, and compliance


## goals and benefits
* the goal of continuous testing is to provide fast and continuous feedback regarding the level of business risk in the latest build or release candidate
* this information can then be used to determine if the software is ready to progress through the delivery pipeline at any given time
* when software quality efforts and testing are aligned with business expectations, test execution produces a prioritized list of actionable tasks (rather than a potentially overwhelming number of findings that require manual review)
  * this helps teams focus their efforts on the quality tasks that will have the greatest impact, based on their organization's goals and priorities


## scope of testing
* continuous testing includes the validation of both functional requirements and non-functional requirements.
  * for testing functional requirements, continuous testing often involves unit tests, api testing, integration testing, and system testing
  * for testing non-functional requirements (to determine if the application meets expectations around performance, security, compliance, etc.), it involves practices such as static code analysis, security testing, performance testing, etc.
* tests should be designed to provide the earliest possible detection (or prevention) of the risks that are most critical for the business or organization that is releasing the software
* teams often find that in order to ensure that test suite can run continuously and effectively assesses the level of risk, it's necessary to shift focus from gui testing to api testing because 1) apis (the "transaction layer") are considered the most stable interface to the system under test, and 2) gui tests require considerable rework to keep pace with the frequent changes typical of accelerated release processes; tests at the API layer are less brittle and easier to maintain


## common practices
* testing should be a collaboration of development, qa, and operations - aligned with the priorities of the line of business - within a coordinated, end-to-end quality process
* tests should be logically-componentized, incremental, and repeatable; results must be deterministic (always produce the same output from a given starting condition or initial state) and meaningful
* all tests need to be run at some point in the build pipeline, but not all tests need be run all the time
* eliminate test data and environment constraints so that tests can run constantly and consistently in production-like environments
* to minimize false positives, minimize test maintenance, and more effectively validate use cases across modern systems with multitier architectures, teams should emphasize api testing over gui testing

## test categories

* Unit: Unit Tests
* Integration: Integration Tests
* Service: Test on service layer (SOAP, REST)
* Functional: tests that want to guarantee the operation against different business rules (happy path, sad path and alternative flows)
* Non-functional tests: performance, load, security, etc...
* Acceptance: acceptance testing (testing focus on the user perspective)
  * Usability
  * accessibility

Aim to create an entire automated test architecture to support the continuous, automated, and least-maintenance run possible with:
* screenshots to evidence the execution of each test, or evidence when an error ocurrs
* logs to analyse and see any error occurred
* reports to show up a feedback about the test execution
* data management for the sensitive data on a test script
* parameterize commonly changed data like URL's, endpoints, etc...


## tools

specific to java:

test category | testing tools
------------ | -------------
unit | junit
integration | junit, arquillian?
service | junit, rest assured, wire mock
functional | junit, selenium
(non-functional) performance | jmeter, gatling
(non-functional) load | jmeter, gatling
(non-functional) security | ?
acceptance | ?
(acceptance) usability | ?
(acceptance) accessibility | pa11y, tenon


## links
* [wikipedia - continuous testing](https://en.wikipedia.org/wiki/Continuous_testing)
* [Trust Your Pipeline: Automatically Testing an End-to-End Java Application] (https://medium.com/@eliasnogueira/trust-your-pipeline-automatically-testing-an-end-to-end-java-application-4a33232180c3)
* [wikipedia - Regression testing](https://en.wikipedia.org/wiki/Regression_testing)
* [Agile testing directions: tests and examples - Brian Marick](http://www.exampler.com/old-blog/2003/08/22/#agile-testing-project-2)

https://upload.wikimedia.org/wikipedia/commons/8/80/Agile_DevOps_Shift_Left_Testing.jpg

https://github.com/in28minutes/java-best-practices/blob/master/pdf/LoadAndPerformanceTestingBestPractices.pdf

https://github.com/in28minutes/java-best-practices/blob/master/pdf/SecuringYourApplication-OWASP.pdf

https://blogs.gov.scot/digital/2016/12/20/accessibility/

http://pa11y.org/

https://tenon.io/
