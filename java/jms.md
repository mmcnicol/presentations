
# Java Message Service (JMS)


## provider (aka MOM, message broker, MQ server) implementations

* [ActiveMQ](http://activemq.apache.org/)
* [RabbitMQ](https://www.rabbitmq.com/)
* [Kafka](https://kafka.apache.org/)

https://content.pivotal.io/rabbitmq/understanding-when-to-use-rabbitmq-or-apache-kafka


## provider features

* reliable delivery
* dead letter queues
* routing (integrate multiple services/apps with non-trivial routing logic)
* high availability
* security
* management tools (a browser-based UI for management and monitoring, plus CLI tools for operators)


## helloworld-jms

https://github.com/jboss-developer/jboss-eap-quickstarts/blob/7.1.0.GA/helloworld-jms/configure-jms.cli


https://github.com/jboss-developer/jboss-eap-quickstarts/blob/7.1.0.GA/helloworld-jms/remove-jms.cli



https://github.com/jboss-developer/jboss-eap-quickstarts/blob/7.1.0.GA/helloworld-jms/src/main/java/org/jboss/as/quickstarts/jms/HelloWorldJMSClient.java
```
/*
 * JBoss, Home of Professional Open Source
 * Copyright 2015, Red Hat, Inc. and/or its affiliates, and individual
 * contributors by the @authors tag. See the copyright.txt in the
 * distribution for a full listing of individual contributors.
 *
 * Licensed under the Apache License, Version 2.0 (the "License");
 * you may not use this file except in compliance with the License.
 * You may obtain a copy of the License at
 * http://www.apache.org/licenses/LICENSE-2.0
 * Unless required by applicable law or agreed to in writing, software
 * distributed under the License is distributed on an "AS IS" BASIS,
 * WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 * See the License for the specific language governing permissions and
 * limitations under the License.
 */
package org.jboss.as.quickstarts.jms;

import java.util.logging.Logger;
import java.util.Properties;

import javax.jms.ConnectionFactory;
import javax.jms.Destination;
import javax.jms.JMSConsumer;
import javax.jms.JMSContext;
import javax.naming.Context;
import javax.naming.InitialContext;
import javax.naming.NamingException;

public class HelloWorldJMSClient {
    private static final Logger log = Logger.getLogger(HelloWorldJMSClient.class.getName());

    // Set up all the default values
    private static final String DEFAULT_MESSAGE = "Hello, World!";
    private static final String DEFAULT_CONNECTION_FACTORY = "jms/RemoteConnectionFactory";
    private static final String DEFAULT_DESTINATION = "jms/queue/test";
    private static final String DEFAULT_MESSAGE_COUNT = "1";
    private static final String DEFAULT_USERNAME = "quickstartUser";
    private static final String DEFAULT_PASSWORD = "quickstartPwd1!";
    private static final String INITIAL_CONTEXT_FACTORY = "org.wildfly.naming.client.WildFlyInitialContextFactory";
    private static final String PROVIDER_URL = "http-remoting://127.0.0.1:8080";

    public static void main(String[] args) {

        Context namingContext = null;

        try {
            String userName = System.getProperty("username", DEFAULT_USERNAME);
            String password = System.getProperty("password", DEFAULT_PASSWORD);

            // Set up the namingContext for the JNDI lookup
            final Properties env = new Properties();
            env.put(Context.INITIAL_CONTEXT_FACTORY, INITIAL_CONTEXT_FACTORY);
            env.put(Context.PROVIDER_URL, System.getProperty(Context.PROVIDER_URL, PROVIDER_URL));
            env.put(Context.SECURITY_PRINCIPAL, userName);
            env.put(Context.SECURITY_CREDENTIALS, password);
            namingContext = new InitialContext(env);

            // Perform the JNDI lookups
            String connectionFactoryString = System.getProperty("connection.factory", DEFAULT_CONNECTION_FACTORY);
            log.info("Attempting to acquire connection factory \"" + connectionFactoryString + "\"");
            ConnectionFactory connectionFactory = (ConnectionFactory) namingContext.lookup(connectionFactoryString);
            log.info("Found connection factory \"" + connectionFactoryString + "\" in JNDI");

            String destinationString = System.getProperty("destination", DEFAULT_DESTINATION);
            log.info("Attempting to acquire destination \"" + destinationString + "\"");
            Destination destination = (Destination) namingContext.lookup(destinationString);
            log.info("Found destination \"" + destinationString + "\" in JNDI");

            int count = Integer.parseInt(System.getProperty("message.count", DEFAULT_MESSAGE_COUNT));
            String content = System.getProperty("message.content", DEFAULT_MESSAGE);

            try (JMSContext context = connectionFactory.createContext(userName, password)) {
                log.info("Sending " + count + " messages with content: " + content);
                // Send the specified number of messages
                for (int i = 0; i < count; i++) {
                    context.createProducer().send(destination, content);
                }

                // Create the JMS consumer
                JMSConsumer consumer = context.createConsumer(destination);
                // Then receive the same number of messages that were sent
                for (int i = 0; i < count; i++) {
                    String text = consumer.receiveBody(String.class, 5000);
                    log.info("Received message with content " + text);
                }
            }
        } catch (NamingException e) {
            log.severe(e.getMessage());
        } finally {
            if (namingContext != null) {
                try {
                    namingContext.close();
                } catch (NamingException e) {
                    log.severe(e.getMessage());
                }
            }
        }
    }
}
```

## how to unit-test JMS code

http://activemq.apache.org/how-to-unit-test-jms-code.html


## Why Use JMS?

https://www.ibm.com/developerworks/library/j-jtp0205/index.html

"Databases are simply not designed for polling or for events. If you must take action relatively quickly after an event occurs or data changes, asynchronous messaging is by far the easier and more efficient way to accomplish this. Whenever you find yourself polling a database for an update, consider using JMS instead."

"Using MQ to get risky operations off the critical path"

Conclusion

"When applied correctly, message queuing (MQ) technology can greatly simplify the processing of complex tasks by facilitating decomposing the task into simple subtasks, and can increase the flexibility and scalability of our applications..."


Introduction to Oracle Advanced Queuing​
https://docs.oracle.com/cd/B10500_01/appdev.920/a96587/qintro.htm

Advanced Queuing is able to meet requirements in the following situations:
* Applications that do not have the resources to handle multiple unprocessed messages arriving simultaneously from external clients or from programs internal to the application.
* Communication links between databases that are not available all the time or are reserved for other purposes. If the system falls short in its capacity to deal with these messages immediately, the application must be able to store the messages until they can be processed.
* Eternal clients or internal programs that are not ready to receive messages that have been processed.


https://www.javaworld.com/article/2074634/java-web-development/should-you-go-with-jms-.html

Should you go with JMS?

"Why JMS isn't always the best solution for distributed system development"

"Only-when-necessary rule of thumb"


When to use JMS, anyway?
https://community.oracle.com/thread/3997458


http://searchmicroservices.techtarget.com/photostory/2240235278/Top-five-use-cases-for-Java-messaging/1/Industry-insiders-share-JMS-use-cases



## management tools


### Hermes JMS

[Hermes JMS](https://github.com/HermesJMS) is a graphical user interface for working with JMS queues.
https://solacelabs.github.io/solace-integration-guides/hermesjms/


### JBoss JMS standalone GUI tool for beginners showing queues and messages (2010)

https://developer.jboss.org/thread/155277


## books

* Beginning Java EE 7, by Antonio Goncalves, 2013.


## links

* [JBOSS EAP 7.1; Developer Materials; helloworld-jms](https://developers.redhat.com/quickstarts/eap/helloworld-jms/)
* [JBOSS EAP 7.1; Quickstarts; helloworld-jms; code on github](https://github.com/jboss-developer/jboss-eap-quickstarts/tree/7.1.0.GA/helloworld-jms)
* [2011; JBOSS 7 AS; Setting up HornetQ JMS](https://www.techartifact.com/blogs/2012/10/jboss-as-7-setting-up-hornetq-jms.html)
* [Should you use JMS in your next enterprise application?](https://www.ibm.com/developerworks/library/j-jtp0205/index.html)
* [Should you go with JMS?](https://www.javaworld.com/article/2074634/java-web-development/should-you-go-with-jms-.html)
* [Introduction to RabbitMQ](https://youtu.be/GoIkHMCXFCU)
* [Java EE 8; The Java EE Tutorial; Overview of the JMS Examples](https://javaee.github.io/tutorial/jms-examples002.html)
* [Java JMS helloworld on JBoss 5.0 AS example](https://examples.javacodegeeks.com/enterprise-java/jms/java-jms-helloworld-on-jboss-example/)
* [wikipedia JMS](https://en.m.wikipedia.org/wiki/Java_Message_Service)
* [wikipedia Apache ActiveMQ](https://en.m.wikipedia.org/wiki/Apache_ActiveMQ)
* [Simple Guide to JMS using ActiveMQ](https://javainsider.wordpress.com/2012/09/25/simple-guide-to-java-message-service-jms-using-activemq/amp/)
* [Advantages of JMS](https://j2eereference.com/advantages-java-message-service-jms/)
* [JMS Patterns with ActiveMQ](http://sujitpal.blogspot.co.uk/2007/12/jms-patterns-with-activemq.html)
* [Apache ActiveMQ REST API](http://activemq.apache.org/rest.html)
* [Enterprise Integration Patterns with ActiveMQ](https://www.slideshare.net/mobile/rajdavies/enterprise-integration-patterns-with-activemq)
* [Apache ActiveMQ Enterprise Integration Patterns](http://activemq.apache.org/enterprise-integration-patterns.html)
* [enterpriseintegrationpatterns.com; messaging patterns](http://www.enterpriseintegrationpatterns.com/patterns/messaging/toc.html)
* [Apache Camel; Components](https://github.com/apache/camel/blob/master/components/readme.adoc)
* [Messaging Anit-Patterns: Part 1](http://sensatic.net/messaging/messaging-anti-patterns-part-1.html)
* [Running an ActiveMQ Broker with Maven](https://www.ivankrizsan.se/2016/02/22/running-an-activemq-broker-with-maven/)
* [O'REILLY Learning Path: Enterprise Messaging Techniques](https://player.oreilly.com/videos/9781491964958)
