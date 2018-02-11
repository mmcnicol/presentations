
# devops - continuous integration


https://www.martinfowler.com/articles/continuousIntegration.html




* continuous integration (CI) is the practice, in software engineering, of merging all developer working copies with a shared mainline several times a day
* it was adopted as part of extreme programming (XP), which did advocate integrating more than once per day, perhaps as many as tens of times per day
* the main aim of CI is to prevent integration problems, referred to as "integration hell" in early descriptions of XP
  * scenario: multiple developers/branches where a checked-out branch has significant changes that means automatic merging might not work
  * avoids last-minute chaos at release dates, when everyone tries to check in their slightly incompatible versions
* constant availability of a "current" build for testing, demo, or release purposes

---

* CI was originally intended to be used in combination with automated unit tests written through the practices of test-driven development
* initially this was conceived of as running all unit tests in the developer's local environment and verifying they all passed before committing to the mainline
* this helps avoid one developer's work-in-progress breaking another developer's copy
* if necessary, partially complete features can be disabled before committing using feature toggles

---

* later elaborations of the concept introduced build servers, which automatically run the unit tests periodically or even after every commit and report the results to the developers
* the use of build servers (not necessarily running unit tests) had already been practised by some teams outside the XP community.
* nowadays, many organisations have adopted CI without adopting all of XP

---

* automatic build script, which can steps such as:
  * compile
  * beautify or uglify/minify: css, javascript
  * compress images
  * extract and format documentation from the source code
  * running automated tests
  * deploy
* triggered on commit to code repository
* or scheduled to run hourly/daily


## jenkins
* "jenkins" is an open source continuous integration tool written in java
* the project was forked from "hudson" after a dispute with oracle
* it is a server-based system running in a servlet container such as apache tomcat
* it can execute automatic build scripts, such as apache maven, in projects as well as arbitrary unix/linux shell scripts and windows batch commands
* builds can be started by various means, including being triggered by commit in a version control system, scheduling via a cron-like mechanism, building when other builds have completed, and by requesting a specific build url


