
http://hibernate.org/

---

http://www.javatips.net/blog/category/hibernate

---


http://hibernate.org/orm/

Hibernate ORM enables developers to more easily write applications whose data outlives the application process. As an Object/Relational Mapping (ORM) framework, Hibernate is concerned with data persistence as it applies to relational databases (via JDBC).

In addition to its own "native" API, Hibernate is also an implementation of the Java Persistence API (JPA) specification. As such, it can be easily used in any environment supporting JPA including Java SE applications, Java EE application servers, Enterprise OSGi containers, etc.

High Performance

Hibernate supports lazy initialization, numerous fetching strategies and optimistic locking with automatic versioning and time stamping. Hibernate requires no special database tables or fields and generates much of the SQL at system initialization time instead of at runtime.

Hibernate consistently offers superior performance over straight JDBC code, both in terms of developer productivity and runtime performance.

Scalability

Hibernate was designed to work in an application server cluster and deliver a highly scalable architecture. Hibernate scales well in any environment: Use it to drive your in-house Intranet that serves hundreds of users or for mission-critical applications that serve hundreds of thousands.

Reliable
Hibernate is well known for its excellent stability and quality, proven by the acceptance and use by tens of thousands of Java developers.




https://vladmihalcea.com/2017/01/18/the-jpa-entitymanager-createnativequery-is-a-magic-wand/
The JPA EntityManager createNativeQuery is a Magic Wand




http://www.developer.com/open/article.php/3559931/Hibernate-Basics.htm

Basic Hibernate Configuration

Hibernate provides two alternative configuration files: a standard Java properties file called hibernate.properties and an XML formatted file called hibernate.cfg.xml. 
It's important to realize that both configuration files perform the same function: configuring the Hibernate service.
If both the hibernate.properties and hibernate.cfg.xml files are found in the application classpath, then hibernate.cfg.xml overrides the settings found in the hibernate.properties file. 

Before configuring Hibernate, you should first determine how the service obtains database connections. Database connections may be provided by the Hibernate framework or from a JNDI DataSource. A third method, user-provided JDBC connections, is also available, but it's rarely used.

Using Hibernate-managed JDBC Connections

The sample configuration file in listing 1 uses Hibernate-managed JDBC connections. You would typically encounter this configuration in a nonmanaged environment, such as a standalone application.

Listing 1. Example hibernate.cfg.xml file

<?xml version="1.0">
<!DOCTYPE hibernate-configuration PUBLIC
"-//Hibernate/Hibernate Configuration DTD 3.0//EN"
"http://hibernate.sourceforge.net/hibernate-configuration-
3.0.dtd">
<hibernate-configuration>
  <session-factory>
    <property name="connection.username">uid</property>
    <property name="connection.password">pwd</property>
    <property name="connection.url">
        jdbc:mysql://localhost/db
    </property>
    <property name="connection.driver_class">
        com.mysql.jdbc.Driver
    </property>
    <property name="dialect">
        org.hibernate.dialect.MySQLDialect
    </property>
    <mapping resource="com/manning/hq/ch03/Event.hbm.xml"/>
    <mapping resource="com/manning/hq/ch03/Location.hbm.xml"/>
    <mapping resource="com/manning/hq/ch03/Speaker.hbm.xml"/>
    <mapping resource="com/manning/hq/ch03/Attendee.hbm.xml"/>
  </session-factory>
</hibernate-configuration>


To use Hibernate-provided JDBC connections, the configuration file requires the following five properties:

connection.driver_class -The JDBC connection class for the specific database
connection.url -The full JDBC URL to the database
connection.username -The username used to connect to the database
connection.password -The password used to authenticate the username
dialect -The name of the SQL dialect for the database

...

The dialect property tells the framework whether the given database supports identity columns, altering relational tables, and unique indexes, among other database-specific details. Hibernate ships with more than 20 SQL dialects, supporting each of the major database vendors, including Oracle, DB2, MySQL, and PostgreSQL.

Hibernate also needs to know the location and names of the mapping files describing the persistent classes. The mapping element provides the name of each mapping file as well as its location relative to the application classpath. There are different methods of configuring the location of the mapping file, which we'll examine later.

...

Creating Hibernate Mapping Definitions

Mapping definitions, also called mapping documents, are used to provided Hibernate with information to persist objects to a relational database. The mapping files also provide support features, such as creating the database schema from a collection of mapping files.

Mapping definitions for persistent objects may be stored together in a single mapping file. Alternatively, the definition for each object can be stored in an individual mapping file. The latter approach is preferred, since storing the definitions for a large number of persistent classes in one mapping file can be cumbersome.

The naming convention for mapping files is to use the name of the persistent class with the hbm.xml extension. The mapping file for the Event class is thus Event.hbm.xml. The Event.hbm.xml file is shown in listing 3.

Listing 3 The Event.hbm.xml mapping file

<?xml version="1.0"?>
<!DOCTYPE hibernate-mapping PUBLIC
     "-//Hibernate/Hibernate Mapping DTD 3.0//EN"
     "http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
<hibernate-mapping package="com.manning.hq.ch03">
    <class name="Event"table="events">
       <id name="id"column="uid"type="long"unsaved-value="null">
          <generator class="native"/>
      </id>
      <property name="name"type="string"length="100"/>
      <property name="startDate"column="start_date" type="date"/>
      <property name="duration"type="integer"/>
      <many-to-one name="location"column="location_id" class="Location"/>
      <set name="speakers">
          <key column="event_id"/>
          <one-to-many class="Speaker"/>
     </set>
     <set name="attendees"/>
         <key column="event_id"/>
         <one-to-many class="Attendee"/>
     </set>
  </class>
</hibernate-mapping>



Hibernate IDs and Generators

The id element describes the primary key for the persistent class as well as how the key value is generated. Each persistent class must have an id element declaring the primary key for the relational table. Let's look at the id element:

<id name="id"column="uid"type="long"unsaved-value="null">
    <generator class="native"/>
</id>

The name attribute defines the property in your persistent class that will be used to store the primary key value. The id element implies that the Event class has a property also named id:

public Long getId(){
    return this.id;
}
public void setId(Long id){
    this.id =id;
}


...

Databases supporting identity columns include Sybase, MySQL, Microsoft SQL Server, and IBM DB2. Oracle, PostgreSQL, and SAP DB support sequence columns.

...

Here's the necessary code to persist an Event instance:

    Configuration cfg =new Configuration();
    SessionFactory factory =cfg.buildSessionFactory();
    Event event =new Event();
    //populate the Event instance
    Session session =factory.openSession();
    session.saveOrUpdate(event);
    session.flush();
    session.close();

...

Retrieving Objects
Suppose you want to retrieve an Event instance from the database. If you have the Event ID, you can use a Session to return it:

    Event event =(Event)session.load(Event.class,eventId);
    session.close();
This code tells Hibernate to return the instance of the Event class with an ID equal to eventId. Notice that you're careful to close the Session, returning the database connection to the pool. There is no need to flush the Session, since you're not persisting objects-only retrieving them. What if you don't know the ID of the object you want to retrieve? This is where HQL enters the picture.

The Session interface allows you to create Query objects to retrieve persistent objects. (In Hibernate 2, the Session interface supported a number of overloaded find methods. They were deprecated in Hibernate 3.) HQL statements are object-oriented, meaning that you query on object properties instead of database table and column names. Let’s look at some examples using the Query interface.

This example returns a collection of all Event instances. Notice that you don't need to provide a select ...clause when returning entire objects:

    Query query =session.createQuery("from Event");
    List events =query.list();

This query is a little more interesting since we're querying on a property of the Event class:

    Query query =session.createQuery("from Event where name ="+
                                    "'Opening Presentation'");
    List events =query.list();

We've hardcoded the name value in the query, which isn't optimal. Let's rewrite it:

    Query query =session.createQuery("from Event where name =?",
                                     "Opening Presentation");
    query.setParameter(0,"Opening Presentation",Hibernate.STRING);
    List events =query.list();

The question mark in the query string represents the variable, which is similar to the JDBC PreparedStatement interface. The second method parameter is the value bound to the variable, and the third parameter tells Hibernate the type of the value. (The Hibernate class provides constants for the built-in types, such as STRING , INTEGER , and LONG , so they can be referenced programmatically.)

...

The Session cache
One easy way to improve performance within the Hibernate service, as well as your applications, is to cache objects. By caching objects in memory, Hibernate avoids the overhead of retrieving them from the database each time. Other than saving overhead when retrieving objects, the Session cache also impacts saving and updating objects. Let's look at a short code listing:

    Session session =factory.openSession();
    Event e =(Event)session.load(Event.class,myEventId);
    e.setName("New Event Name");
    session.saveOrUpdate(e);
    //later,with the same Session instance
    Event e =(Event)session.load(Event.class,myEventId);
    e.setDuration(180);
    session.saveOrUpdate(e);
    session.flush();

This code first retrieves an Event instance, which the Session caches internally. It then does the following: updates the Event name, saves or updates the Event instance, retrieves the same Event instance (which is stored in the Session cache), updates the duration of the Event,and saves or updates the Event instance. Finally, you flush the Session.

All the updates made to the Event instance are combined into a single update when you flush the Session. This is made possible in part by the Session cache.

The Session interface supports a simple instance cache for each object that is loaded or saved during the lifetime of a given Session. Each object placed into the cache is keyed on the class type, such as The Session cache com.manning.hq.ch03.Event, and the primary key value. However, this cache presents some interesting problems for unwary developers.

...

Cache Providers

As we mentioned earlier, caching is a common method used to improve application performance. Caching can be as simple as having a class store frequently used data, or a cache can be distributed among multiple computers. The logic used by caches can also vary widely, but most use a simple least recently used (LRU) algorithm to determine which objects should be removed from the cache after a configurable amount of time.

Before you get confused, let's clarify the difference between the Session–level cache, also called the first–level cache, and what this section covers. The Session–level cache stores object instances for the lifetime of a given Session instance. The caching services described in this section cache data outside of the lifetime of a given Session. Another way to think about the difference is that the Session cache is like a transactional cache that only caches the data needed for a given operation or set of operations, whereas a second–level cache is an application-wide cache.

...

Inheritance

Inheritance is a fundamental concept of object-oriented languages. Through inheritance, objects can inherit the state and behavior of their ancestor, or superclass. The most common use of object inheritance in applications is to create a generic base type with one or more specialized subclasses. Persisting a class hierarchy can be difficult, since each hierarchy can have its own unique requirements.

To address the problems found in hierarchy persistence, Hibernate supports three different inheritance persistence strategies:

Table per class hierarchy
Table per subclass
Table per concrete class

Each mapping strategy is incrementally more complicated.

## hibernate 5.2
* [hibernate 5.2 user guide | jboss](http://docs.jboss.org/hibernate/orm/5.2/userguide/html_single/Hibernate_User_Guide.html)
* [use java 8 optional hibernate](https://thorben-janssen.com/use-java-8-optional-hibernate/)

## links
* [Hibernate Tutorial 01 - Introduction To Hibernate | Java Brains](https://www.youtube.com/watch?v=Yv2xctJxE-w&list=PL_5aB2ncz1K8swf-bMC6cQpfzF12VxpHt)
* [Annotation based Hibernate Hello World example using Maven build tool and SQLite database](http://www.srccodes.com/p/article/7/Annotation-based-Hibernate-Hello-World-example-using-Maven-build-tool-and-SQLite-database)
