
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

## entity relationships

There is a mappedBy element on the @OneToOne, @OneToMany, and @ManyToMany annotations, but not on the @ManyToOne annotation.


### @OneToOne Unidirectional

```java
@Entity
public class Parent {
  @Id
  private Long id;
  private Child child;
}

@Entity
public class Child {
  @Id
  private Long id;
}
```

```sql
create table PARENT (
 ID BIGINT not null,
 CHILD_ID BIGINT,
 primary key (ID),
 foreign key (CHILD_ID) references CHILD(ID)
 );

create table CHILD (
 ID BIGINT not null,
 primary key (ID)
 );
```

with JPA, if you do not annotate an attribute, the default mapping rules are applied. So, by default,
the name of the foreign key column is CHILD_ID. Also notice that, in the DDL, the CHILD_ID column is nullable by
default, meaning that, by default, a one-to-one association is mapped to a zero (null value) or one.

To customize the mapping, you can use two annotations. The first one is @OneToOne (that’s because the
cardinality of the relation is one), and it can modify some attributes of the association itself such as the way it has to be
fetched.

The other is @JoinColumn. It is used to customize the join column (foreign key column), meaning the foreign key, of the owning side.

```java
@Entity
public class Parent {
  @Id
  private Long id;
  @OneToOne // could add (fwtch = FetchType.LAZY)
  @JoinColumn(name="child_fk", nullable = false) // foreign key renamed
  private Child child;
}
```

### @OneToMany Unidirectional

```java
@Entity
public class Parent {
  @Id
  private Long id;
  private List<Child> children;
}

@Entity
public class Child {
  @Id
  private Long id;
}
```
By default, one-to-many unidirectional relationships use a join table to keep the
relationship information, with two foreign key columns.

If you don’t like the join table and foreign key names, or if you are mapping to an existing table, you can use JPA
annotations to redefine these default values.

```java
@Entity
public class Parent {
  @Id
  private Long id;
  @OneToMany
  @JoinTable(name = "parent_child_join",
    joinColumns = @JoinColumn(name = "parent_fk"),
    inverseJoinColumns = @JoinColumn(name = "child_fk")
  private List<Child> children;
}
```

```sql
create table PARENT_CHILD_JOIN (
  PARENT_FK BIGINT not null,
  CHILD_FK BIGINT not null,
  primary key (PARENT_FK, CHILD_FK),
  foreign key (CHILD_FK) references CHILD(ID),
  foreign key (PARENT_FK) references PARENT(ID)
);
```

The default rule for a one-to-many unidirectional relationship is to use a join table, but it is very easy (and useful
for legacy databases) to change to using foreign keys. The Order entity has to provide a @JoinColumn annotation
instead of a @JoinTable.

```java
@Entity
public class Parent {
  @Id
  private Long id;
  @OneToMany(fetch = FetchType.EAGER)
  @JoinColumn(name = "parent_fk")
  private List<Child> children;
}
```
The foreign key is renamed to PARENT_FK by the annotation and exists in the target table (CHILD).

@ManyToMany Bidirectional

In the Java world, each entity will have a collection of target entities. In the relational world, the only way to map a
many-to-many relationship is to use a join table.


## ordering relationships

With one-to-many or many-to-many relationships, your entities deal with collections of objects. On the Java side, these
collections are usually unordered. Neither do relational databases preserve any order in their tables. Therefore, if you
want an ordered list, it is necessary to either sort your collection programmatically or use a JPQL query with an Order
By clause. JPA has easier mechanisms, based on annotations that can help in ordering relationships.

### @OrderBy

### @OrderColumn



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


## attribute converters

A Converter must implement the javax.persistence.AttributeConverter interface.
* [How to persist LocalDate and LocalDateTime with JPA](https://youtu.be/vnTUJFQCLfs)
* [How to implement a Converter?](https://www.thoughts-on-java.org/jpa-21-how-to-implement-type-converter/)


## how to implement soft/logical delete
* [How to implement a soft delete with Hibernate](https://youtu.be/2Ttsh8JUH5g)
* [The best way to soft delete with Hibernate](https://vladmihalcea.com/the-best-way-to-soft-delete-with-hibernate/)


## java 8 date time support
* [What’s new in JPA 2.2 – Java 8 Date and Time Types](https://vladmihalcea.com/whats-new-in-jpa-2-2-java-8-date-and-time-types/)
* [How to map java.time.Year and java.time.Month with JPA and Hibernate](https://vladmihalcea.com/java-time-year-month-jpa-hibernate/)


## jakarta persistence

* [Jakarta Persistence](https://projects.eclipse.org/projects/ee4j.jpa)

### java ee 7 jpa
* [java ee 7 jpa samples](https://github.com/javaee-samples/javaee7-samples/tree/master/jpa)

### jakarta 8 persistence
* [jakarta specifications persistence 2.2](https://jakarta.ee/specifications/persistence/2.2/)
* [What's new in JPA 2.2 - Stream the result of a Query execution | Vlad Mihalcea](https://vladmihalcea.com/whats-new-in-jpa-2-2-stream-the-result-of-a-query-execution/)

### jakarta 9 persistence
* [jakarta specifications persistence 3.0](https://jakarta.ee/specifications/persistence/3.0/)

## links
* [difference between jpa hibernate eclipselink](https://www.thoughts-on-java.org/difference-jpa-hibernate-eclipselink/)
* [A beginner’s guide to flush strategies in JPA and Hibernate | Vlad Mihalcea](https://vladmihalcea.com/a-beginners-guide-to-jpahibernate-flush-strategies/)
* [Query pagination with JPA and Hibernate | Vlad Mihalcea](https://vladmihalcea.com/query-pagination-jpa-hibernate/#more-10933)
* [Getting started with Hibernate | Thorben Janssen](https://www.youtube.com/watch?v=6TPDK6MOkz4)
* [JPA & Hibernate: Entity Lifecycle Model | Thorben Janssen](https://youtu.be/Y7PpjerZkc0)
* [Implementing Batch Jobs with Hibernate | Thorben Janssen](https://www.youtube.com/watch?v=COrDelJMWqw)
