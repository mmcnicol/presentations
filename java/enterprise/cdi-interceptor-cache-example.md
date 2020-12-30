# cdi interceptor cache example

```
publuc class DocumentStoreClient {

   @Interceptors(CacheInterceptor.class)
   public Object get(long id) {
      // ...
   }
   
}
```

```
@Interceptor
publuc class CacheInterceptor {
   private static final Logger LOGGER = ...
   
   @Inject
   ...

   @AroundInvoke
   public Object aroundInvoke(InvokationContext ctx) {
      // can use ctx.getMethod(), ctx.getParameters()
      cacheKey = ...
      cache = ...
      CacheEntry entry = cache.get(cacheKey);
      if(entry == null) {
         // cache miss
         Object value = ctx.proceed();
         entry = new CacheEntry(value);
         cache.put(cacheKey, entry);
      } else {
         // cache hit
      }
      return entry.getValue();
   }
   
}
```

## links
* [caching made easy with cdi and infinispan](https://paluch.biz/blog/115-caching-made-easy-with-cdi-and-infinispan.html)
