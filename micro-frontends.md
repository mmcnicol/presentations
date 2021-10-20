# micro-frontends

* micro-frontends enable splitting of monolithic frontends into independent and smaller micro applications
* are concerned with the presentation layer of a modern web application
* enable the decomposition of the front-end into individual and semi-independent front-ends, and creating independent services that interact together
* are not concerned with separating the frontend and back-end completely from each other
* micro-frontends share the main principles, benefits, and issues of microservices


## micro applications, mini applications
* have an isolated/dedicated business layer
* can utilise a dedicated/independant database schema
* use/require common services
  * logging, audit, error
  * security (authentication, authorisation)
  * access to application/3rd-party/cached data


## perceived benefits, motivations, pros
* for developers
  * can reduce the overall complexity of the frontend
  * can enable developers to quickly and effectively deliver value to customers
  * developer attention - work on smaller projects (reduce cognitive load, reduce build time)
* for production
  * reduce release size/risk - avoid releasing the whole app - release smaller things which reflect just what has changed - deploy independently


## issues, drawbacks, cons
* for developers
  * increased code duplication
  * increased overhead
  * requires careful planning
* for production
  * increased payload size of the application
  * more complexity for observability & monitoring

