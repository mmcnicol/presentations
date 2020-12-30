# cdi interceptor cache example

```
public class DocumentStoreClient {

   @Interceptors(CacheInterceptor.class)
   public Object get(long id) {
      // ...
   }
   
}
```

```
@Interceptor
public class CacheInterceptor {
   private static final Logger LOGGER = ...
   
   @Inject
   ...
   
   // An interceptor class must have a public, no-argument constructor.
   public CacheInterceptor() {
   }

   @AroundInvoke
   public Object aroundInvoke(InvokationContext ctx) {
      // can use ctx.getMethod(), ctx.getParameters()
      Object[] parameters = ctx.getParameters();
      Long id = (Long) parameters[0];
      
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
