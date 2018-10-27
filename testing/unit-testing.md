# unit testing

## definition

"verify that a known fixed input produces a known fixed output"

* it should be deterministic
* try to avoid accessing external resources such as network, file system, database
* control time
* write your tests first
  * test 1st hides implementation and avoids exposing internal implementation details. it avoids brittle, tightly coupled tests.
* make your tests unitary - each test tests exactly one thing
* share setup in a fixture, not in the same method
* you can have multiple test classes per target class

## Testing Behavior vs. Testing Implementation

When I test for behavior, I’m saying:
“I don’t care what the answer is, just make sure you do this thing while figuring it out.”

When I test for implementation, I’m saying:
“I don’t care how you come up with the answer, just make sure that the answer is correct under this set of circumstances”

In actual practice, what ends up happening is that a test looks for the result of the method (good), but it also makes assertions about how that answer was derived (not-so-good) by relying too much on mock and stubs.

## links
* [effective unit testing](https://youtu.be/mjlEhR-pFnY)
* [how just about everyone gets unit testing wrong](https://www.javaworld.com/article/2892225/testing-debugging/how-just-about-everyone-gets-unit-testing-wrong.html)

