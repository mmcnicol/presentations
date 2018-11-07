# observability

## using plain java?

decorator design pattern - lets you attach responsibilities to objects at runtime.  
https://github.com/iluwatar/java-design-patterns/tree/master/decorator  
https://airbrake.io/blog/design-patterns/structural-design-patterns-decorator  
http://www.dsc.ufcg.edu.br/~jacques/cursos/map/recursos/Decorate%20your%20Java%20code.htm

## using Java EE?

decorators - implement additional business logic for a bean  
https://docs.oracle.com/javaee/7/tutorial/cdi-adv-examples005.htm

alternatives - choose between two beans at deployment time  
https://docs.oracle.com/javaee/7/tutorial/cdi-adv-examples001.htm

interceptors - are used in conjunction with Java EE managed classes to allow developers to invoke interceptor methods on an associated target class, in conjunction with method invocations or lifecycle events. Common uses of interceptors are logging, auditing, and profiling.  
https://docs.oracle.com/javaee/6/tutorial/doc/gkigq.html  
Using Interceptors:  
https://docs.oracle.com/javaee/6/tutorial/doc/gkedm.html  
Using Interceptors in CDI Applications:  
https://docs.oracle.com/javaee/6/tutorial/doc/gkhjx.html


## metrics

### java libraries

[Micrometer](https://micrometer.io/) provides a simple facade over the instrumentation clients for the most popular monitoring systems, allowing you to instrument your JVM-based application code without vendor lock-in. Think SLF4J, but for metrics.

https://prometheus.io/docs/instrumenting/clientlibs/

https://github.com/prometheus/client_java


### java agents

https://docs.oracle.com/javase/7/docs/api/java/lang/instrument/Instrumentation.html

https://docs.oracle.com/javase/8/docs/api/java/lang/instrument/package-summary.html

https://stackoverflow.com/questions/10659610/how-to-instrument-java-methods

http://karunsubramanian.com/websphere/how-to-instrument-a-java-application-with-appdynamics/


### commercial

https://www.ej-technologies.com/products/jprofiler/overview.html


## tracing

Distributed tracing is a mechanism to track requests through a network of distributed systems in order to create transparency and shed light on the sometimes complex interactions and behavior of those systems. 

https://github.com/Nike-Inc/wingtips

https://zipkin.io/pages/existing_instrumentations

https://github.com/openzipkin/brave

https://github.com/smoketurner/dropwizard-zipkin

https://github.com/openzipkin/brave/tree/master/instrumentation




