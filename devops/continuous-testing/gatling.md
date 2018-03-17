
# gatling

## What is Gatling ?

Gatling is a stress tool. Development is currently focusing on HTTP support.

## motivation

* Finding fancy GUIs not that convenient for describing stress tests, what you want is a friendly expressive DSL?
* Wanting something more convenient than huge XML dumps to store in your source version control system?

## advantages

* Free
* Efficient
* Defines a DSL designed for expressing load tests, easy to learn scripts just reading.
Meaningful charts
* Graphite & Jenkins Integration
* Supports CSV input files to access random data for Data-Driven tests.

## examples

```
package demo

import io.gatling.core.Predef._
import io.gatling.http.Predef._
import scala.concurrent.duration._

class BasicSimulation extends Simulation {

  val httpConf = http
    .baseURL("https://api.github.com") // Here is the root for all relative URLs
    .acceptHeader("application/json")
    .userAgentHeader("Mozilla/5.0 (Macintosh; Intel Mac OS X 10.8; rv:16.0) Gecko/20100101 Firefox/16.0")

  val scn = scenario("Scenario Name") // A scenario is a chain of requests and pauses
    .exec(http("request_1")
      .get("/users/mmcnicol/repos"))
    .pause(1)

  setUp(scn.inject(atOnceUsers(1)).protocols(httpConf))
}

```

pause(1) // sleep for 1 second

pause(1, 5 seconds) // sleep for random number of seconds between 1 and 5

atOnceUsers(1) // 1 simulated user to begin executing the scenario immediately

atOnceUsers(10) // 10 simulated users to begin executing the scenario immediately

rampUsers(2) over (4 seconds) // 2 simulated users to begin executing the scenario spread over 4 seconds

rampUsers(2).over(4 seconds) // TODO: check if this is old syntax?



# links

Stéphane Landelle - Load Testing Done Right with Gatling https://youtu.be/VUPTaPms210

Stresstests with Gatling by Niko Köbler https://youtu.be/gOZvtBYzIVc

https://github.com/gatling/gatling

https://gatling.io/documentation/

https://gatling.io/docs/current/extensions/maven_plugin/

https://www.thoughtworks.com/insights/blog/gatling-take-your-performance-tests-next-level

http://clardeur.blogspot.co.uk/2013/07/getting-started-gatling-alternative-jmeter.html

https://www.ivankrizsan.se/2016/03/27/creating-a-scala-project-with-maven-dependency-management-for-gatling-testing-in-intellij-idea/
https://www.ivankrizsan.se/2016/04/16/introduction-to-load-testing-with-gatling-part-1/
https://www.ivankrizsan.se/2016/04/24/introduction-to-load-testing-with-gatling-part-2/
https://www.ivankrizsan.se/2016/04/26/introduction-to-load-testing-with-gatling-part-3/
https://www.ivankrizsan.se/2016/05/06/introduction-to-load-testing-with-gatling-part-4/

https://automationrhapsody.com/performance-testing-with-gatling-integration-with-maven/

https://www.swtestacademy.com/gatling-installation-configuration/

http://www.hascode.com/2016/05/load-testing-web-applications-with-gatling-and-maven/

