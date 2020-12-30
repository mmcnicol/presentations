# cdi (context & dependancy injection)

2009: CDI 1.0 released (java ee 6)  
2013: CDI 1.1 released (java ee 7, jboss 7.0/7.1?)  
2016: CDI 2.0 released (java ee 8, jboss 7.2)  

since CDI 1.1, CDI is activated by default

## contexts (a way to manage a Bean's lifecycle)
@Dependent (the default, depends on the context of the Bean to which it is injected)  
@ApplicationScoped, @SessionScoped, @RequestScoped,  
@ConversationScoped  
@Singleton

note: @SessionScoped and @ConversationScoped must be serializable

## inject

## qualifier

there are 3 reserved qualifiers:
@Default
@Any
@Named

## interceptor
* [Learning Java EE 8: Interceptors | packtpub.com](https://www.youtube.com/watch?v=ZDnctWW301k)
* [Apache TomEE and CDI (Interceptors) | Alex Soto Bueno](https://www.youtube.com/watch?v=jLAd_Y2ztrU)

## decorator
* [Design Patterns and Best Practices in Java EE 8 : Decorator Pattern | packtpub.com](https://www.youtube.com/watch?v=0iLqRq8CyOk)
* [Apache TomEE and CDI (Decorators) | Alex Soto Bueno](https://www.youtube.com/watch?v=s8TJFub2m7c)


## links
* [Chapter 7. Contexts and Dependency Injection | redhat jboss eap docs](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/7.2/html/development_guide/contexts_and_dependency_injection)
* [Contexts and Dependency Injection | Getting Started with MicroProfile](https://www.youtube.com/watch?v=Q8jHRDu9Fbo)
* [Introduction to CDI | Virtual JBoss User Group](https://www.youtube.com/watch?v=E0lhfKIHclc)
