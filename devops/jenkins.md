

Pipeline is quickly establishing itself as the direction that Jenkins jobs are going, enabling the definition of a complete CD pipeline in a single job; 
Pipeline as Code via the “Jenkinsfile”; 


https://fosdem.org/2017/schedule/event/declarative_pipeline/

---

http://www.bogotobogo.com/DevOps/Jenkins/images/Intro_install/jenkins-the-definitive-guide.pdf

---

edit job configuration
build environment = 1.0.$(BUILD_NUMBER)

---

edit job configuration
pre step: execute  shell

echo info.build.version=1.0.$BUILD_NUMBER >> src/main/resources/application.properties

---



## java project build version

Continuous Delivery friendly Maven versions
https://blog.sebastian-daschner.com/entries/cd-friendly-maven-versions



# links

https://learning.javaspecialists.eu/p/transition-to-continuous-delivery-with-enterprise-java/


