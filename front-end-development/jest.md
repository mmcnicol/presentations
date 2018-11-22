# jest

a javaScript testing solution.

* Instant Feedback - fast interactive watch mode runs only test files related to changed files.
* Snapshot Testing - can capture snapshots of React trees or other serializable values to simplify testing and to analyze how state changes over time.
* Fast and sandboxed - Jest parallelizes test runs across workers to maximize performance. Console messages are buffered and printed together with test results. Sandboxed test files and automatic global state resets for every test so no two tests conflict with each other.
* Built-in code coverage reports - easily create code coverage reports using --coverage. No additional setup or libraries needed! Jest can collect code coverage information from entire projects, including untested files.
* Powerful mocking library - powerful mocking library for functions and modules.

so, can:
* unit test
* browser test - using puppeteer (similar to selenium) & the chrome web browser

## matchers
Jest uses "matchers" to let you test values in different ways.
* [using-matchers](https://jestjs.io/docs/en/using-matchers)

## Mock Functions
Mock functions make it easy to test the links between code by erasing the actual implementation of a function, capturing calls to the function (and the parameters passed in those calls), capturing instances of constructor functions when instantiated with new, and allowing test-time configuration of return values.
There are two ways to mock functions: Either by creating a mock function to use in test code, or writing a manual mock to override a module dependency.
* [mock-functions](https://jestjs.io/docs/en/mock-functions)


## links
* [jest website](https://jestjs.io/en/)
* [separating unit and integration tests in jest](https://medium.com/coding-stones/separating-unit-and-integration-tests-in-jest-f6dd301f399c​)
