
# monitoring and observability

is about instrumentation. 

using tools with ability to ask questions. when something happens, can we ask questions?
* is the system generally slow?
* is there a backlog in a queue?

should be:
* cheap to instrument
* easy to explore
* reliable and trustworthy

don't spend all your time testing. use some for instrumenting.

production is just the start.


## monitoring

application performance management (APM) is the monitoring and management of performance and availability of software applications.

expected level of service

the translation of IT metrics into business meaning e.g. value.

is about alterts. are things working within thresholds?

agent-based vs agentless monitoring

example tools:
* [nagios](https://www.nagios.org/)
* [app dynamics](https://www.appdynamics.com/)


## observability

observability is a measure of how well internal states of a system can be inferred from knowledge of its external outputs.

the 4 pillars of observability:
* health checks
* metrics
* logging
* tracing

each pillar complements each other.

monitoring and resilience:
* health checks
* metrics (alerts)

debugging and logging:
* metrics (queries)
* tracing
* logs
* events


### health check

think traffic lights. is something up or down. what is the status of dependancies?

health checks are generally very simple binary checks:
* a deployed web application
* a database
* an internal service
* an external (3rd party) service
* caches
* a process
* maybe even critial files

typically pulled by a collector, a high-availability store.

example tools:
* [prometheus](https://prometheus.io/)


### metrics

dashboards, with ability toset rules, thresholds, and send alerts.

hardware-level:
* memory
* disk space
* CPU

application-level:
* error rates
* latency
* response times

business-level:
* number of purchases (e-commerce)
* number of documents sent

trade-offs: not sufficient for debugging.

example tools:
* [grafana](https://grafana.com/)
* [kibana](https://www.elastic.co/products/kibana)


#### alerts

An actionable alert is when:
1. Something breaks
2. A customer notices
3. You're the best person to fix it
4. You can fix it now
If we have 4/4 then wake me up

source: [a devopsdaysnz quote from Katrina Clokie](https://twitter.com/katrina_tester/status/1059195138621169664?s=03)


### logging

aggregated, centralised.

logs are cheap, they are just text.

provide context.

structured logging:
* when? date time
* what? error message
* where? service name
* platform: geographical server location, JDK version
* who? user id, customer id
* version? release, commit id, build number
* trace id

example tools:
* [logstash](https://www.elastic.co/products/logstash)
* [elasticsearch](https://www.elastic.co/products/elasticsearch)


### tracing

ability to see timeline chain of method/service calls and time taken

request tracing.

example tools:
* [zipkin](https://zipkin.io/)
* [jaeger](https://www.jaegertracing.io/)


## links
* [How to Build Observable Distributed Systems](https://youtu.be/ACL_YVPD3gw)
* [monitoring your java services with dropwizard health checks](https://www.stubbornjava.com/posts/monitoring-your-java-services-with-dropwizard-health-checks)
* [metrics.dropwizard.io](http://metrics.dropwizard.io/4.0.0/) Metrics is a Java library which gives you unparalleled insight into what your code does in production.
* [We can do better than percentile latencies](https://medium.com/theburningmonk-com/we-can-do-better-than-percentile-latencies-2257d20c3b39)
* [Observability-Driven Development (is the Future of DevOps) by Charity Majors](https://youtu.be/z2JoDjoZCM4)
* [Observability pre-release: Using Prometheus to test and fix new software - GitHub Universe 2018](https://youtu.be/6gh9CcC_i5c)
