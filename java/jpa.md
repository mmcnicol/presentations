
# jpa

## persistence context

### persistence unit

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


