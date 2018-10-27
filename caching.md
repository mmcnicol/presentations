# application caching


## definition

"a store of things that will be required in the future, and can be retreived rapidly"

a map (key/value mappings) with:
* capacity control (via eviction)
* freshness control (via expiry)

## where is caching used?

* cpu - modern cpus have 3 layers of cache (L1, L2, L3)
* disk
* browser
* cdn
* jvm

## glossary
* hit - when the cache returns a value
* miss - when the cache does not return a value
* cold / hot - when the cache is empty / full.
* system of record (database, web service, result of complex computation)

## strategies
* prepopulate cache when you start the server
* use a distributed/clustered cache
* configure cache max size

## caching patterns
* no caching
* cache aside
* cache through

## metrics: what to measure?
* cache usage: empty? full?
* hit ratio: hits / (misses + hits)
* hit rate: hits / second

## jvm
* jsr-107
* example java caching framework/library: ehcache (started as a 2nd level cache for hibernate)
* use visualJVM to view javax.cache metrics/statistics for ehcache
* you can export metrics to prometheus

## links
* [caching in applications still matters](https://youtu.be/-oNd0FN5R6I)
* [write-through write-around write-back cache explained](http://www.computerweekly.com/feature/Write-through-write-around-write-back-Cache-explained)

