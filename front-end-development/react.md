# react

React is a JavaScript library for building user interfaces.

## why use react?
* react enables developers to 
  * declaratively describe their user interfaces
  * model the state of those interfaces
* components
  * enable deveopers to break down a complex UI into simple reusable components
  * components are your lego pieces
  * components can contain other components
* simplicity
  * easy to learn. fast learning curve.
  * react is just javaScript, there is a very small api to learn. 
  * react is a javascript library. it’s not a framework.
  * react only deals with the view layer
* error messages at build time are helpful and concise (compared to java stacktraces)


* [Why ReactJS is gaining so much popularity these days](https://medium.com/@thinkwik/why-reactjs-is-gaining-so-much-popularity-these-days-c3aa686ec0b3)
* [Yes, React is taking over front-end development. The question is why.](https://medium.freecodecamp.org/yes-react-is-taking-over-front-end-development-the-question-is-why-40837af8ab76)
* [What Is ReactJS and Why Should We Use It?](https://www.c-sharpcorner.com/article/what-and-why-reactjs/)
* [7 Reasons why you should use React](https://stories.jotform.com/7-reasons-why-you-should-use-react-ad420c634247)


## ecosystem
* [navigating the react ecosystem](https://www.toptal.com/react/navigating-the-react-ecosystem)


## starter kits
* [starter kits](https://reactjs.org/community/starter-kits.html)


## testing
* [Introducing the react-testing-library](https://blog.kentcdodds.com/introducing-the-react-testing-library-e3a274307e65)
* [How to build sturdy React apps with TDD and the React Testing Library](https://medium.freecodecamp.org/how-to-build-sturdy-react-apps-with-tdd-and-the-react-testing-library-47ad3c5c8e47)
* [Test-Driven Development in React with Cypress - Josh Justice](https://vimeo.com/298277470)
* [how we landed on jest snapshot testing for javascript](https://blog.grommet.io/post/2016/09/01/how-we-landed-on-jest-snapshot-testing-for-javascript)


## error handling
* [error handling in react 16](https://reactjs.org/blog/2017/07/26/error-handling-in-react-16.html)
* [error handling in react best practices](https://stackoverflow.com/questions/36897434/error-handling-in-react-best-practices)


## how to make ajax requests?
* [AJAX and APIs](https://reactjs.org/docs/faq-ajax.html)
* [axios react](https://alligator.io/react/axios-react/)
* [How to make AJAX requests in React? – Bartosz Szczeciński – Medium](https://medium.com/@baphemot/how-to-make-ajax-requests-in-react-a6a52bb5a8b1)
* [AJAX Requests in React: How and Where to Fetch Data](https://daveceddia.com/ajax-requests-in-react/)


## server-side vs client-side rendering
* [server-side vs client-side rendering in React apps](https://hackernoon.com/server-side-vs-client-side-rendering-in-react-apps-443efd6f2e87)
* [Demystifying server-side rendering in React](https://medium.freecodecamp.org/demystifying-reacts-server-side-render-de335d408fe4)


## state
* [Storing JSON data in React with setState](https://medium.com/@brettcelestre/storing-json-data-in-react-with-setstate-3b588b74dcce)
* [React State Museum - Gant Laborde](https://vimeo.com/298276409 )


### redux
* provides a single store; a single source of truth
* there is only one single object where you keep all the application data
* any change on the store (data) will trigger a render for related components and the view is always kept in sync with data

* [redux](https://redux.js.org/)


## how to add inline style
https://reactjs.org/docs/dom-elements.html  
also see:  
* [radium](https://www.npmjs.com/package/radium)
* [Getting started with CSS modules in React](https://blog.pusher.com/css-modules-react/)
* [babel-plugin-react-css-modules](https://github.com/gajus/babel-plugin-react-css-modules)


## components
* [react docs; component](https://reactjs.org/docs/react-component.html)
* [Our Engineering Experience with React and Storybook](https://auth0.com/blog/our-engineering-experience-with-react-and-storybook/)


## the component lifecycle
* [react lifecycle methods diagram](http://projects.wojtekmaj.pl/react-lifecycle-methods-diagram/)


## individual react ui components
* [table](https://www.npmjs.com/package/rc-table)
* [react-table](https://www.npmjs.com/package/react-table)
* [datepicker](https://www.npmjs.com/package/rc-datepicker)
* [menu](https://www.npmjs.com/package/rc-menu)
* [dialog](https://www.npmjs.com/package/rc-dialog)
* [notification](https://www.npmjs.com/package/rc-notification)
* [toastify](https://www.npmjs.com/package/react-toastify)


### react-table - How to link the whole row in the table?
https://github.com/react-tools/react-table/issues/206


### how to compare the popularity of components
https://www.npmtrends.com/react-bs-datatable-vs-react-handsontable-vs-react-list-vs-react-table-vs-reactable


## collections of react ui components
* [23 best react ui component libraries and frameworks](https://hackernoon.com/23-best-react-ui-component-libraries-and-frameworks-250a81b2ac42)
* [material ui](https://material-ui.com/) // react components that implement google's material design.
* [material design](https://www.npmjs.com/package/react-md)
* [responsive-ui](https://www.npmjs.com/package/react-responsive-ui)
* [govuk-react-components](https://github.com/lennym/govuk-react-components)
* [primefaces.org/primereact](https://www.primefaces.org/primereact/)
* [jqwidgets.com/react](https://www.jqwidgets.com/react/) // commercial


### how to show in-app messages using material-ui
https://medium.freecodecamp.org/how-to-show-informational-messages-using-material-ui-in-a-react-web-app-5b108178608


## forms
* [jsonforms.io](https://jsonforms.io/)
* [react-jsonschema-form](https://github.com/mozilla-services/react-jsonschema-form)


## efficiently render large lists and tabular data
* [react-virtualized](https://github.com/bvaughn/react-virtualized)


## how to include 3rd party libraries

### moment.js
http://momentjs.com/docs/  
https://www.npmjs.com/package/moment  
https://github.com/react-tools/react-table/issues/515  

npm install moment

```
import Moment from "moment";
...
Moment(d.date).local().format("DD/MM/YYYY")
```

### Integrating React with Other Libraries
* [Integrating with Other Libraries – React](https://reactjs.org/docs/integrating-with-other-libraries.html)
* [add react to a website](https://reactjs.org/docs/add-react-to-a-website.html)
* [integrate reactjs into jquery webapps](https://winterbe.com/posts/2015/08/24/integrate-reactjs-into-jquery-webapps/)
* [how to sprinkle reactjs into an existing web application](https://scotch.io/tutorials/how-to-sprinkle-reactjs-into-an-existing-web-application)
* [Bring React to an existing app](https://youtu.be/8zmmYxyc9Uc)
* [react without jsx](https://reactjs.org/docs/react-without-jsx.html)
* [react without npm babel or webpack](https://medium.com/@chrislewisdev/react-without-npm-babel-or-webpack-1e9a6049714)


## security
* [Exploiting Script Injection Flaws in ReactJS Apps](https://medium.com/dailyjs/exploiting-script-injection-flaws-in-reactjs-883fb1fe36c1)
* [The Most Common XSS Vulnerability in React.js Applications](https://medium.com/node-security/the-most-common-xss-vulnerability-in-react-js-applications-2bdffbcc1fa0)


## links
* [reactjs website](https://reactjs.org/)
* [react howto](https://github.com/petehunt/react-howto)
