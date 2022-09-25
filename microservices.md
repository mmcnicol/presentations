# microservices

## golden rules
* use a mono repo
* each services should have the same structure
* use a template to create a new services
** so you can concentrate on just writing business logic
* use event-driven, to divide complex processes into independant chunks of work
* make it easy to update common functionality
* write tests to lock the behaviour of your services' API

## pros
* technical debt easier to control in individual services
* they naturally keep many things simple (individual services)
** because a large number of individually simple and loosely-coupled systems are more resilient than a small number of individually complex and tightly-coupled systems
* hot deployment of individual services (components)
* elasticity

## cons
* overkill for a small system which would be easier as a monolith
* deployment more complex (compared to a single monolith)
* good tracing & logging is necessary
* cascading failures & retry storms
* platform is complex e.g. kubernetes/docker (service discovery)
* easy to get burned by microservices gone wrong
* seems impossible due to large number of services
* not a silver bullet

## links
* [article: microservices | Martin Fowler](https://www.martinfowler.com/articles/microservices.html)
* [Martin Fowler – Microservices](https://youtu.be/2yko4TbC8cI)
* [Principles Of Microservices by Sam Newman](https://youtu.be/PFQnNFe27kU)
* [Building Microservice Architectures | Neal Ford | Voxxed Days Vienna 2016](https://youtu.be/pjN7CaGPFB4)
* [Microservices in action at the Dutch National Police: Bert Jan Schrijver](https://vimeo.com/233788662)
* [Here's a diagram of two microservices and their shared database](https://twitter.com/mathiasverraes/status/711168935798902785?lang=en)
* [Event-based Architecture and Implementations with Kafka and Atom | Eberhard Wolff | GOTO 2018](https://youtu.be/Ecg7lvvm8aU)
* [Avoiding Microservice Megadisasters | Jimmy Bogard | NDC Conferences](https://www.youtube.com/watch?v=gfh-VCTwMw8)
* [Microservices in Go | Matt Heath | GOTO 2016](https://www.youtube.com/watch?v=WiCru2zIWWs)
* [How to Structure Your Microservices | Kat Zień | GopherCon Europe 2020](https://www.youtube.com/watch?v=KCyMtx5ev80)
