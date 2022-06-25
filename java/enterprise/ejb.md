# Enterprise JavaBeans (EJB)

2013: EJB 3.2 released (Java EE 7, JBoss EAP 7)

Types of Enterprise Beans:
* Session Beans
* Message Driven Beans

In case of Stateful beans, a new instance of the bean is returned every time a client performs a lookup. In case of Stateless beans, any one bean from the pool is returned.

## Session Beans

The lifecycle of a session bean instance is, naturally, managed by the EJB container. Depending on how they’re managed, sessions beans can be in either of the following states:
* Stateless
* Stateful
* Singelton

## Message Driven Beans

A message-driven bean or MDB is an enterprise bean that allows you to process messages asynchronously. This type of bean normally acts as a JMS message listener, which is similar to an event listener but receives JMS messages instead of events.

They are in many ways similar to a Stateless session bean but they are not invoked by a client. instead, they are event-driven.

## specification versions
* [EJB 3.2](https://download.oracle.com/otndocs/jcp/ejb-3_2-fr-spec/index.html)

## links
* [EJBs? Still Great In Java EE 7 (The Lifecycle) | Adam Bien | 2012](https://www.youtube.com/watch?v=2aZwW3ZVWRk)
* [Learning Java EE 8: Asynchronous EJBs| Sebastian Daschner | packtpub.com | 2018](https://www.youtube.com/watch?v=LksyRzlQwZk)
