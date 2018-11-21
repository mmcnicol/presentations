# browser testing

## selenium


## cypress.io
* Electron is the default browser.
* many browsers such as Firefox, Safari, and Internet Explorer are not currently supported.
* cypress supports both BDD (expect/should) and TDD (assert) style assertions.
* when running in interactive mode using "cypress open", cypress watches the filesystem for changes to your spec files. soon after adding or updating a test cypress will reload it and run all of the tests in that spec file.
* Cypress comes built in with the ability to stub and spy with cy.stub(), cy.spy() or modify your application’s time with cy.clock() - which lets you manipulate Date, setTimeout, setInterval, amongst others.

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
* [core concepts; cypress is simple](https://docs.cypress.io/guides/core-concepts/introduction-to-cypress.html#Cypress-Is-Simple)
* [core concepts; dynamically generate tests](https://docs.cypress.io/guides/core-concepts/writing-and-organizing-tests.html#Dynamically-Generate-Tests)
* [core concepts; when elements are missing](https://docs.cypress.io/guides/core-concepts/introduction-to-cypress.html#When-Elements-Are-Missing)
* [core concepts; custom environment variables](https://docs.cypress.io/guides/guides/continuous-integration.html#Custom-Environment-Variables)
* [Test-Driven Development in React with Cypress - Josh Justice](https://vimeo.com/298277470)
* [Testing React Components using Storybook and Cypress](https://medium.com/@mtiller/testing-react-components-using-storybook-and-cypress-1689a27f55aa)


## links
* [Cypress vs Selenium WebDriver: Better, or just different?](https://applitools.com/blog/cypress-vs-selenium-webdriver-better-or-just-different)
