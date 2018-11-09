# streams

* stream let you process data in a declarative way
* use stream operations to express sophisticated data processing queries
* streams can leverage multi-core architectures without you having to write a single line of multithread code
* several operations (filter, sorted, map, collect) can be chained together to form a pipeline

a quick example:
given "transactions" is defined as "List<Transaction>":
```
List<Integer> transactionsIds = transactions.stream()
   .filter(t -> t.getType() == Transaction.GROCERY)
   .sorted(comparing(Transaction::getValue).reversed())
   .map(Transaction::getId)
   .collect(toList());
```

## links
* [OTN; Processing Data with Java SE 8 Streams, Part 1](https://www.oracle.com/technetwork/articles/java/ma14-java-se-8-streams-2177646.html)
* [OTN; Part 2: Processing Data with Java SE 8 Streams](https://www.oracle.com/technetwork/articles/java/architect-streams-pt2-2227132.html)
