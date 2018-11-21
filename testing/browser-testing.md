# browser testing

## selenium


## cypress.io
* Electron is the default browser.
* many browsers such as Firefox, Safari, and Internet Explorer are not currently supported.
* cypress supports both BDD (expect/should) and TDD (assert) style assertions.
* when running in interactive mode using "cypress open", cypress watches the filesystem for changes to your spec files. soon after adding or updating a test cypress will reload it and run all of the tests in that spec file.

```javascript
describe('...', function () {

  it('...', function () {
    //...
  })

it.only('...', function () {
    //...
  })

})
```

* [cypress.io website](https://www.cypress.io/)
* [Test-Driven Development in React with Cypress - Josh Justice](https://vimeo.com/298277470)
* [Testing React Components using Storybook and Cypress](https://medium.com/@mtiller/testing-react-components-using-storybook-and-cypress-1689a27f55aa)
* [core concepts; dynamically generate tests](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests.html#Dynamically-Generate-Tests)

## links
* [Cypress vs Selenium WebDriver: Better, or just different?](https://applitools.com/blog/cypress-vs-selenium-webdriver-better-or-just-different)
