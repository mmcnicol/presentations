
# java



## general

@SuppressWarnings("unchecked")



## stopwatch

```
long start = System.nanoTime();
// do something
long end = System.nanoTime();
System.out.println("Execution time: " + (end - start) / 1000000 + "ms");
```


## json parsing

https://www.sitepoint.com/php-style-json-parsing-in-java-with-jsoniter/
PHP-Style JSON Parsing in Java with Jsoniter (February 27, 2017)



## swagger

http://www.adam-bien.com/roller/abien/entry/jax_rs_get_swagger_json


Simple example on how to quickly generate @SwaggerApi with jaxrs-analyzer-maven-plugin (by @DaschnerS ) and show with swagger-ui webjar. No swagger maven dependencies needed at all
https://github.com/afrunt/examples/tree/master/misc/jax-rs-analyzer


## CompletableFuture

* [CompletableFuture_- The_Promises_of_Java_-_Venkat_Subramaniam](https://vimeo.com/267930513)


## override equals method (e.g. in a DTO)

```
@Override
    public boolean equals(Object o) {
        if (this == o) return true;
        if (o == null || getClass() != o.getClass()) 
            return false;
        ClassA that = (ClassA) o;
        return Objects.equals(fieldA, that.fieldA) &&
               Objects.equals(fieldB, that.fieldB);
    }
```


