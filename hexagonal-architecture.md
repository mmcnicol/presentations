# hexagonal architecture

hexagonal architecture divides work inside and outside of an app instead of into layers. 

the inside part consists of **use cases** and the **domain model** it’s built upon.

(in a 'layered architecture', what we would call application and domain layers)

the outside part consists of everything else
* UI
* database
* file I/O
* web services
* messaging
* and other stuff.

the connection between the inside and the outside part of our application is realized via abstractions called **ports** and their implementation counterparts called **adapters**.

the natural counterpart of a port in java is an interface.

the natural counterpart of an adapter is the implementation.

by hiding certain technical details behind a port, we remove some clutter from our use case/domain logic and gain more flexibility as the port can have multiple adapter implementations.

there are some principles to be followed:
* the inside part knows nothing about the outside part
* you should be able to use any adapter that fits a given port
* no use case or domain logic goes to the outside part

benefits:
* making our application logic agnostic to the delivery model - thanks to this, the most crucial logic of our application is pure and clean and can be understood without the clutter of different technologies used to make it work in the production environment

# links
* [Hexagonal Architecture Is Powerful](https://dzone.com/articles/hexagonal-architecture-is-powerful)

