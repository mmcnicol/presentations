# micro-frontends

* micro-frontends enable splitting of monolithic frontends into individual and semi-independent and smaller units
* are concerned with decomposition of the presentation layer
* aim to divide the presentation layer (application) vertically
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
  * feature switches, settings/configuration
  * user session, user session timeout
  * access to application/3rd-party/cached data


## perceived benefits, motivations, pros
* for developers
  * can reduce the overall complexity of the frontend
  * can enable developers to quickly and effectively deliver value to customers
  * reduce cognitive load - work on smaller projects - avoid working on a huge code base
  * potentially reduce need to strictly adhere to a single project structure/style (grouping & naming of packages, classes)
  * promotes establishing a bounded context (a DDD concept)
  * build isolated and loosely coupled services
  * potentially promotes failure isolation
  * potentially reduce project build time
* for production
  * reduce release size/risk - avoid releasing the whole app - release smaller things which reflect just what has changed - deploy independently


## issues, drawbacks, cons
* for developers
  * potentially increased code duplication
  * increased overhead
  * requires careful planning
* for production
  * increased payload size of the application
  * more complexity for observability & monitoring


## is an alternative to
* component driven development
* monolithic applications, where code becomes tightly coupled


## links
* [Motivations, benefits, and issues for adopting Micro-Frontends: A Multivocal Literature Review](https://www.sciencedirect.com/science/article/pii/S0950584921000549)
* [Micro Frontends - The Nitty Gritty Details or Frontend, Backend | Michael Geers | Micro CPH](https://www.youtube.com/watch?v=wCHYILvM7kU)
* [The Problems Micro Frontends Won't Solve That No One Wants to Talk About | Jennifer Wadella | NDC Conferences](https://www.youtube.com/watch?v=KfezmwfTu7Y)
* [Loosely Coupled - Micro-Frontends And Capital One’s Contact Centers | Steve Husak & Noah Mandelbaum | The Linux Foundation](https://www.youtube.com/watch?v=rLF_N0f2Z9U)
* [Micro-Frontends in AWS | Luca Mezzalira | NDC London 2023](https://www.youtube.com/watch?v=Wn1Cj7785i8)

