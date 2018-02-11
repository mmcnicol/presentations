

matthew@laptop:~$ mvn -version
Apache Maven 3.0.4
Maven home: /usr/share/maven
Java version: 1.6.0_35, vendor: Sun Microsystems Inc.
Java home: /usr/lib/jvm/java-6-openjdk-i386/jre
Default locale: en_GB, platform encoding: UTF-8
OS name: "linux", version: "3.2.0-4-686-pae", arch: "i386", family: "unix"
matthew@laptop:~$ 



mvn archetype:generate


groupId: com.mongodb
packageName: com.mongodb
package: com.mongodb
artifactId: M101J
basedir: /home/matthew/Dropbox/dev/java
version: 1.0-SNAPSHOT


mvn clean compile exec:java -Dexec.mainClass=com.mongodb.App

mvn clean compile exec:java -Dexec.mainClass=com.mycompany.mavenproject1.App




---

To clean the local cache try using the dependency plug-in

mvn dependency:purge-local-repository



