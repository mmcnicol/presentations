
# devops


> "DevOps is the combination of cultural philosophies, practices, and tools that increases an organization's ability to deliver applications and services at high velocity: evolving and improving products at a faster pace than organizations using traditional software development and infrastructure management processes. This speed enables organizations to better serve their customers and compete more effectively in the market."
> --- AWS website


* devops is intended to be a cross-functional mode of working
* there are multiple techniques/tools:
  * code - code development and review, source code management tools, code merging
  * build - continuous integration tools, build status
  * test - continuous testing tools that provide feedback on business risks
  * package - artifact repository, application pre-deployment staging
  * release - change management, release approvals, release automation
  * configure - infrastructure configuration and management, "infrastructure as code" tools
  * monitor - applications performance monitoring, end–user experience
* some categories are more essential in a devops toolchain than others; especially continuous integration (e.g. jenkins) and infrastructure as code (e.g. puppet)


![devops diagram](devops-svg.png "devops diagram")


## goals
* the goals of devops span the entire delivery pipeline. they include:
  * improved deployment frequency
  * faster time to market
  * Lower failure rate of new releases
  * Shortened lead time between fixes
  * Faster mean time to recovery (in the event of a new release crashing or otherwise disabling the current system)
* simple processes become increasingly programmable and dynamic, using a devops approach
* devops aims to maximize the predictability, efficiency, security, and maintainability of operational processes. very often, automation supports this objective


## culture
* devops is more than just a tool or a process change; it inherently requires an organizational culture shift. this cultural change is especially difficult, because of the conflicting nature of departmental roles:
  * operations - seeks organizational stability
  * developers - seek change
  * testers - seek risk reduction
* getting these groups to work cohesively is a critical challenge in enterprise devops adoption


## agile
* the need for devops arose from the increasing success of agile software development, as that led to organizations wanting to release their software faster and more frequently
* as they sought to overcome the strain this put on their release management processes, they had to adopt patterns such as application release automation, continuous integration tools, and continuous delivery


## devops practices/techniques
* [continuous integration](continuous-integration/README.md)
* [continuous testing](continuous-testing/README.md)
* [continuous deployment](continuous-deployment/README.md)
* microservices
* configuration management
* infrastructure as code
* monitoring and Logging


## links
* [wikipedia; devops](https://en.wikipedia.org/wiki/DevOps)
* [AWS; What is DevOps?](https://aws.amazon.com/devops/what-is-devops/)
* []nfoq.com; presentation; gov-uk-devops](https://www.infoq.com/presentations/gov-uk-devops)


