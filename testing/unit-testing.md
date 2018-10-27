# unit testing

## definition

"verify that a known fixed input produces a known fixed output"

## principles
* tests should be deterministic
* try to avoid accessing external resources such as network, file system, database
* control time (local time, local timezone)
* write your tests first
  * test 1st hides implementation and avoids exposing internal implementation details. it avoids brittle, tightly coupled tests.
* make your tests unitary - each test tests exactly one thing
* share setup in a fixture, not in the same method
* you can have multiple test classes per model/target class (class under test)
* a single test should run in a second or less
* every unit test should run in a minute or less
* seperate larger/slower tests into additional test suites
* fail fast. run slowest tests last (e.g. integration tests).
* write a failing test before you fix a bug
  * if the test passes, the bug isn't what you think it is
* use continuous integration (e.g. jenkins)

## Testing Behavior vs. Testing Implementation
* In most cases, tests should focus on testing your code's public API, and your code's implementation details shouldn't need to be exposed to tests.
* Tests that are independent of implementation details are easier to maintain since they don't need to be changed each time you make a change to the implementation.

## links
* [effective unit testing](https://youtu.be/mjlEhR-pFnY)
* [Testing on the Toilet: Test Behavior, Not Implementation](https://testing.googleblog.com/2013/08/testing-on-toilet-test-behavior-not.html)
* [how just about everyone gets unit testing wrong](https://www.javaworld.com/article/2892225/testing-debugging/how-just-about-everyone-gets-unit-testing-wrong.html)

