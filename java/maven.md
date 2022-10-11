
# maven

mvn -version

mvn archetype:generate

mvn clean compile exec:java -Dexec.mainClass=com.mongodb.App

mvn clean compile exec:java -Dexec.mainClass=com.mycompany.mavenproject1.App




--- to clean the local cache try using the dependency plug-in

mvn dependency:purge-local-repository



## links

http://maven.apache.org/what-is-maven.html

http://www.baeldung.com/maven-dependency-scopes

https://www.petrikainulainen.net/programming/tips-and-tricks/creating-profile-specific-configuration-files-with-maven/

* [Maven, my life is short! | Peter Palaga | Devoxx 2022](https://www.youtube.com/watch?v=Gwmmz_T6THA)
