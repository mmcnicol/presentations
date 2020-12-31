# JavaServer Faces (JSF) UI framework

## internationalization

example: faces-config.xml
```
<?xml version="1.0" encoding="UTF-8"?>
<faces-config version="2.2"
	xmlns="http://xmlns.jcp.org/xml/ns/javaee"
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee 
	http://xmlns.jcp.org/xml/ns/javaee/web-facesconfig_2_2.xsd">
	<application>
		<locale-config>
			<default-locale>en</default-locale>
			<supported-locale>en</supported-locale>
		</locale-config>
		<resource-bundle>
			<base-name>messages</base-name>
			<var>msg</var>
		</resource-bundle>
	</application>
</faces-config>
```

example: src\main\resources\messages.properties
```
# a comment line
home.greeting.text=Hello World!
```

example: src\main\resources\messages_en.properties
```
# a comment line
home.greeting.text=Hello World!
```

example: index.xhtml
```
<!DOCTYPE html>
<html xmlns="http://www.w3.org/1999/xhtml" 	
	xmlns:h="http://xmlns.jcp.org/jsf/html">
	<h:head>
		<title>internationalization test page</title>
	</h:head>
	<h:body>
		<h1>#{msg['home.greeting.text']}</h1>
	</h:body>
</html>
```

## version 2.2

A new feature in JSF 2.2 is the ability to create stateless views. 

JSF 2.2 introduced new namespaces, which can be specified for supplying pass-through elements, pass-through attributes, or both within HTML pages. Using these new features, HTML5 elements can be treated as JSF components, or JSF components can pass through to the browser without interpretation by JSF components or renderers. HTML5 pages can use JSF backing beans in the same manner as a standard JSF view, enabling seamless interactivity with JSF.

## links
* [PrimeFaces in the Enterprise](https://www.oracle.com/technetwork/articles/java/java-primefaces-2191907.html)
* [PrimeFaces in the Enterprise, Part 2: Mobile Solutions for the Enterprise](https://www.oracle.com/technetwork/articles/java/java-primefaces-pt2-2340750.html)
* [HTML5 and JSF](https://www.oracle.com/technetwork/articles/java/enterprise-html5-2227136.html)
