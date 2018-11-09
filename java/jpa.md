
# jpa

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
|jpa concept|database concept|
|---|---|
|persisting|inserting|
|updating|updating|
|removing|deleting|
|loading|selecting|


### remove

```
public Parent delete(Parent parent) {
   return entityManager.remove(parent);
}
```

### save

```
public Parent save(Parent parent) {
   return entityManager.merge(parent);
}
```

### find

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


### criteria builder

https://github.com/javaee-samples/javaee7-samples/blob/master/jpa/criteria/src/main/java/org/javaee7/jpa/criteria/MovieBean.java



## links
* [java ee 7 jpa samples](https://github.com/javaee-samples/javaee7-samples/tree/master/jpa)
* [difference between jpa hibernate eclipselink](https://www.thoughts-on-java.org/difference-jpa-hibernate-eclipselink/)


