
# Java Persistence API (JPA)

## entity

* must have the annotation @Entity (@javax.persistence.Entity)
* use the @Table annotation if the class name differs from the actual table name in the database
* must have a no-arg constructor, that has to be public or protected
* contains attributes (private fields with getters & setters)
* use the @Column annotation if an attribute name differs from the actual column name in the database table
* optionally, can have business methods
* one attribute must have the annotation @Id (@javax.persistence.Id)

example:
```
@Temporal(TemporalType.DATE)
private Date dateOfBirth;
@Temporal(TemporalType.TIMESTAMP)
private Date creationDate;
```

example:
```
@Transient
private Integer age;
```

example:
```
@Enumerated(EnumType.STRING)
private Result result;
```


## persistence context

### persistence unit

the persistence unit is the bridge between the persistence context and the database.  
it is defined ina file named "persistence.xml".  
It does the following:
* the <class> tag lists all the entities that could be managed in the persistence context
* it also gives all the information to physically connect to the database (using properties)
  * in an application-managed environment, transaction-type="RESOURCE_LOCAL"
  * in a container-managed environment, the persistence.xml would define a data source instead of the database connection properties and set the transaction type to JTA, transaction-type="JTA"

in JPA 2.1, some properties of the persistence.xml file have been standardized - they all start with javax.persistence such as "javax.persistence.jdbc.url"
   
https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/native-sql-resultset-mapping/src/main/resources/META-INF/persistence.xml

for a data source:  
https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/datasourcedefinition-webxml-pu/src/main/resources/META-INF/persistence.xml


### data source

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/datasourcedefinition-webxml-pu/src/main/webapp/WEB-INF/web.xml

using an annotation:  
https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/datasourcedefinition-annotation-pu/src/main/java/org/javaee7/jpa/datasourcedefinition_annotation_pu/config/DataSourceDefinitionConfig.java


### jndi context

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/jndi-context/src/main/java/org/javaee7/jpa/jndi/context/EmployeeBean.java


## entity manager

The operations made to entities fall into four categories which correspond to the equivalent database operations:

| jpa concept | database concept |
| --- | --- |
| persisting | inserting |
| updating | updating |
| removing | deleting |
| loading | selecting |


### persist/add (insert)
from a JPA perspective, an entity is new when it has never been associated with a database row, meaning that there is no table record in the database to match the entity in question.
```
public Parent add(Parent parent) {
   return entityManager.persist(parent); // only for new entities
}
```

### merge (update)
merging is required only for detached JPA entities.

```
public Parent save(Parent parent) {
   return entityManager.merge(parent);
}
```

### remove (delete)

```
public Parent delete(Parent parent) {
   return entityManager.remove(parent);
}
```

### load/find (select)
the EntityManager's find method lets you retrieve a single entity instance based on the entity's id passed in as the parameter.
```
public Parent getParentById(Long id) {
   return entityManager.find(Parent.class, id);
}
```


### query (JPQL)

```
List<Customer> arr_cust = (List<Customer>)em.createQuery("SELECT c FROM Customer c")
   .getResultList(); 
```

```
Integer cust_id =2;
Customer cust = (Customer)em.createQuery("SELECT c FROM Customer c WHERE c.cust_id=:cust_id")
   .setParameter("cust_id", cust_id)
   .getSingleResult();
```

```
Integer cust_id =2;
String cust_name = (String)em.createQuery("SELECT c.cust_name FROM Customer c WHERE c.cust_id=:cust_id")
   .setParameter("cust_id", cust_id)
   .getSingleResult(); 
```

If needed, set the maximum number of instances to retrieve and/or specify the position of the first instance to retrieve, using the setMaxResults and/or setFirstResult Query's methods.

* [Querying JPA Entities with JPQL and Native SQL](https://www.oracle.com/technetwork/articles/vasiliev-jpql-087123.html)

query (JPQL); named query

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/default-datasource/src/main/java/org/javaee7/jpa/defaultdatasource/EmployeeService.java


### query (criteria API, aka Object-Oriented Queries)

new in JPA 2.0

criteria builder

example:
```
CriteriaBuilder builder = em.getCriteriaBuilder();
CriteriaQuery<Customer> criteriaQuery = builder.createQuery(Customer.class);
Root<Customer> c = criteriaQuery.from(Customer.class);
criteriaQuery.select(c).where(builder.equal(c.get("firstName"), "Smith"));
Query query = em.createQuery(criteriaQuery).getResultList();
List<Customer> customers = query.getResultList();
```

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/criteria/src/main/java/org/javaee7/jpa/criteria/MovieBean.java


### query (native query)

The main reason to use JPA native queries rather than JDBC calls is because the result of the query will be automatically converted back to entities.

example:
```
Query query = em.createNativeQuery("SELECT * FROM customer", Customer.class);
List<Customer> customers = query.getResultList();
```

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/native-sql-resultset-mapping/src/main/java/org/javaee7/jpa/nativesql/resultset/mapping/EmployeeBean.java


### query (stored procedures)

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/storedprocedure/src/main/java/org/javaee7/jpa/storedprocedure/Movie.java

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/storedprocedure/src/main/java/org/javaee7/jpa/storedprocedure/MovieBean.java


## caching

The entity manager is a first-level cache used to process data comprehensively for the database and to cache short-lived entities.

all JPA implementations use a performance cache (a.k.a. a second-level cache) to optimize database access, queries, joins, and so on.

example:
```
@Entity
@Cacheable(true)
public class Customer {
...
```

If you decide to mark an entity as cacheable, you then need to inform the provider which caching mechanism to use. The way to do this with JPA is to set the shared-cache-mode attribute in the persistence.xml file.

## versioning

when you persist an entity for the first time in the database, it will get the version number 1. Later, if you update an attribute and commit this change to the database, the entity version will get the number 2, and so on.

an entity can access the value of its version property but must not modify it.


## callbacks

Each life cycle has a "pre" and "post" event that can be intercepted by the entity manager to invoke a business method.

@PrePersist  
@PostPersist  
@PreUpdate  
@PostUpdate  
@PreRemove  
@PostRemove  
@PostLoad  


## listeners

Entity listeners are used to extract the business logic to a separate class and share it between other entities. An entity listener is just a POJO on which you can define one or more life-cycle callback methods. To register a listener, the entity needs to use the @EntityListeners annotation.


## links
* [java ee 7 jpa samples](https://github.com/javaee-samples/javaee7-samples/tree/master/jpa)
* [difference between jpa hibernate eclipselink](https://www.thoughts-on-java.org/difference-jpa-hibernate-eclipselink/)
* [A beginner’s guide to flush strategies in JPA and Hibernate](https://vladmihalcea.com/a-beginners-guide-to-jpahibernate-flush-strategies/)


