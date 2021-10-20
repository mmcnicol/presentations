# micro-frontends

* micro-frontends enable splitting of monolithic frontends into individual and semi-independent and smaller units
* are concerned with decomposition of the presentation layer
* share the main principles, benefits, and issues of microservices


## micro applications, mini applications
* enable splitting of monolithic applications into individual and semi-independent and smaller micro applications
* are concerned with decomposition of the presentation layer, business layer, and database access layer
* are not concerned with separating the frontend and back-end completely from each other
* have an isolated/dedicated business/domain layer
* can utilise a dedicated/independant database schema
* can be accessed on their own, or integrated into a parent/container/skelaton application
  * if accessed on their own, require certain mandatory inputs (context)
* share the main principles, benefits, and issues of microservices
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


## links
* [Motivations, benefits, and issues for adopting Micro-Frontends: A Multivocal Literature Review](https://www.sciencedirect.com/science/article/pii/S0950584921000549)

