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


# links


