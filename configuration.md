# configuration

application configuration management still remains a problematic topic for many, with solutions reinvented and customized for specific situations and use cases. 

possible sources of configuration data:
* datasource / database
* system properties
* system environment variables
* configuration / settings text files
* at runtime by supplying optional command line parameters
* application code

generic requirements:
* the majority of applications need to be configured based on a running environment.
* ideally it should be possible to modify configuration data from outside an application so that the application itself does not need to be repackaged.
* if the same property is defined in multiple locations, a policy should be used to specify which one of the values will effectively be used.
* under some circumstances, when a property value changes, the changed value should be fed into the application without the need for restarting the application.
* ideally, enviroment specific property values should not be located/stored in the code repository along with application source code.
* sensitive property values should not be located/stored in a code repository along with application source code. for example to code in the open, to enable open source code to be published.

examples of sensitive property values:
* secret passwords
* secret tokens
* secret encryption / hash keys
* service urls


## links
* [microprofile config](https://github.com/eclipse/microprofile-config)


