
# Java Persistence API (JPA)

## entity

* must have the annotation @Entity (@javax.persistence.Entity)
* use the @Table annotation if the class name differs from the actual table name in the database
* must have a no-arg constructor, that has to be public or protected
* contains attributes (private fields with getters & setters)
* use the @Column annotation if an attribute name differs from the actual column name in the database table
* optionally, can have business methods
* one attribute must have the annotation @Id (@javax.persistence.Id)




## persistence context

### persistence unit

persistence.xml

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


### named query

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/default-datasource/src/main/java/org/javaee7/jpa/defaultdatasource/EmployeeService.java


### named stored procedure

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/storedprocedure/src/main/java/org/javaee7/jpa/storedprocedure/Movie.java

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/storedprocedure/src/main/java/org/javaee7/jpa/storedprocedure/MovieBean.java


### native query

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/native-sql-resultset-mapping/src/main/java/org/javaee7/jpa/nativesql/resultset/mapping/EmployeeBean.java


### JPQL

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

### criteria builder

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/criteria/src/main/java/org/javaee7/jpa/criteria/MovieBean.java



## links
* [java ee 7 jpa samples](https://github.com/javaee-samples/javaee7-samples/tree/master/jpa)
* [difference between jpa hibernate eclipselink](https://www.thoughts-on-java.org/difference-jpa-hibernate-eclipselink/)
* [A beginner’s guide to flush strategies in JPA and Hibernate](https://vladmihalcea.com/a-beginners-guide-to-jpahibernate-flush-strategies/)


