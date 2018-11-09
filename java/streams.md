# streams

* stream let you process data in a declarative way
* use stream operations to express sophisticated data processing queries
* streams can leverage multi-core architectures without you having to write a single line of multithread code
* several operations (filter, sorted, map, collect) can be chained together to form a pipeline
* aggregate operations: streams support SQL-like operations and common operations from functional programing languages, such as filter, map, reduce, find, match, sorted, and so on. 

example #1:
given "transactions" is defined as "List<Transaction>":
```
List<Integer> transactionsIds = transactions.stream()
   .filter(t -> t.getType() == Transaction.GROCERY)
   .sorted(comparing(Transaction::getValue).reversed())
   .map(Transaction::getId)
   .collect(toList());
```

example#2:
```
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8);
List<Integer> twoEvenSquares = 
    numbers.stream()
           .filter(n -> {
                    System.out.println("filtering " + n); 
                    return n % 2 == 0;
                  })
           .map(n -> {
                    System.out.println("mapping " + n);
                    return n * n;
                  })
           .limit(2)
           .collect(toList());
```

## filtering
there are several operations that can be used to filter elements from a stream: 
* filter(Predicate): Takes a predicate (java.util.function.Predicate) as an argument and returns a stream including all elements that match the given predicate
* distinct: Returns a stream with unique elements (according to the implementation of equals for a stream element)
* limit(n): Returns a stream that is no longer than the given size n
* skip(n): Returns a stream with the first n number of elements discarded 


## Finding and matching
a common data processing pattern is determining whether some elements match a given property.  
you can use the anyMatch, allMatch, and noneMatch operations to help you do this.  
in addition, the Stream interface provides the operations findFirst and findAny for retrieving arbitrary elements from a stream.  
they can be used in conjunction with other stream operations such as filter.  
both findFirst and findAny return an Optional object.


## mapping
streams support the method map, which takes a function (java.util.function.Function) as an argument to project the elements of a stream into another form.  
the function is applied to each element, “mapping” it into a new element.


## reducing
repeatedly applies an operation (for example, adding two numbers) on each element until a result is produced.



## links
* [OTN; Processing Data with Java SE 8 Streams, Part 1](https://www.oracle.com/technetwork/articles/java/ma14-java-se-8-streams-2177646.html)
* [OTN; Part 2: Processing Data with Java SE 8 Streams](https://www.oracle.com/technetwork/articles/java/architect-streams-pt2-2227132.html)