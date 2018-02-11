


http://sparkjava.com/documentation.html




Port
By default, Spark runs on port 4567. If you want to set another port use port. This has to be done before using routes and filters:

port(9090); // Spark will run on port 9090




Embedded web server
Standalone Spark runs on an embedded Jetty web server.



https://github.com/perwendel/spark-template-engines/tree/master/spark-template-handlebars


https://sparktutorials.github.io/2015/04/14/getting-started-with-spark-and-docker.html



Static Files
You can assign a folder in the classpath serving static files with the staticFiles.location method. Note that the public directory name is not included in the URL.
A file /public/css/style.css is made available as http://{host}:{port}/css/style.css

// root is 'src/main/resources', so put files in 'src/main/resources/public'
staticFiles.location("/public"); // Static files





