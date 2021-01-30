# Optional

Java SE 8 introduces a new class called java.util.Optional

> public final class Optional<T>
> extends Object
> 
> A container object which may or may not contain a non-null value. If a value is present, isPresent() will return true and get() will return the value.
> 
> Additional methods that depend on the presence or absence of a contained value are provided, such as orElse() (return a default value if value not present) and ifPresent() (execute a block of code if the value is present).
> 
> This is a value-based class; use of identity-sensitive operations (including reference equality (==), identity hash code, or synchronization) on instances of Optional may have unpredictable results and should be avoided.
> 
> Since:
> 1.8

## examples

Here is an empty Optional:

Optional<someObj> sc = Optional.empty();

And here is an Optional with a non-null value:

SomeObj someObj = new SomeObj();
Optional<SomeObj> sc = Optional.of(someObj);

Also, by using ofNullable, you can create an Optional object that may hold a null value:

Optional<SomeObj> sc = Optional.ofNullable(someObj);

### Do Something If a Value Is Present

Optional<SomeObj> someObj = ...;
someObj.ifPresent(System.out::println);

You no longer need to do an explicit null check; it is enforced by the type system. If the Optional object were empty, nothing would be printed.

You can also use the isPresent() method to find out whether a value is present in an Optional object. In addition, there's a get() method that returns the value contained in the Optional object, if it is present. Otherwise, it throws a NoSuchElementException. The two methods can be combined, as follows, to prevent exceptions:

if(someObj.isPresent()){
  System.out.println(someObj.get());
}

However, this is not the recommended use of Optional (it's not much of an improvement over nested null checks), and there are more idiomatic alternatives, which we explore below.

### Default Values and Actions

SomeObj someObj = maybeSomeObj.orElse(new SomeObj("defaut"));

or,

SomeObj someObj = maybeSomeObj.orElseThrow(IllegalStateException::new);

### Rejecting Certain Values Using the filter Method

Often you need to call a method on an object and check some property. For example, you might need to check whether the USB port is a particular version. To do this in a safe way, you first need to check whether the reference pointing to a USB object is null and then call the getVersion() method, as follows:

SomeObj someObj = ...;
if(someObj != null && "3.0".equals(someObj.getVersion())){
  System.out.println("ok");
}

This pattern can be rewritten using the filter method on an Optional object, as follows:

Optional<SomeObj> maybeSomeObj = ...;
maybeSomeObj.filter(someObj -> "3.0".equals(someObj.getVersion()).ifPresent(() -> System.out.println("ok"));

...


### a return example

if(String.isBlank(someObj)) {
  return Optional.of(someObj);
} else {
  return Optional.empty();
}

could be rewritten as:

return Optional.of(someObj).filter(not(String::isBlank))








## links
* [Tired of Null Pointer Exceptions? Consider Using Java SE 8's "Optional"!](https://www.oracle.com/technical-resources/articles/java/java8-optional.html)
