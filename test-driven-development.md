# test-driven-development (TDD)


## the TTD cycle

* write a test
* see it fail
* write some code to make the test pass
* see the test pass


## Testing Behavior vs. Testing Implementation

When I test for behavior, I’m saying:
“I don’t care what the answer is, just make sure you do this thing while figuring it out.”

When I test for implementation, I’m saying:
“I don’t care how you come up with the answer, just make sure that the answer is correct under this set of circumstances”

In actual practice, what ends up happening is that a test looks for the result of the method (good), but it also makes assertions about how that answer was derived (not-so-good) by relying too much on mock and stubs.


## links
* [Test-driven development](https://en.wikipedia.org/wiki/Test-driven_development)
* [What are your thoughts on Test-driven Development? What are the pros and cons?](https://www.quora.com/What-are-your-thoughts-on-Test-driven-Development-What-are-the-pros-and-cons/answer/James-Grenning-1?srid=zUfj)
* [TDD: The Bad Parts — Matt Parker](https://youtu.be/xPL84vvLwXA)
