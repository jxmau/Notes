<h1> Deploy a Java application </h1>

<h2> Java Application and Environment Variable </h2>

<h4> To get var in Java </h4>

```java

// To get one variable
System.getenv("VAR_NAME");

// To get all the variables as an HashMap
System.getenv();

```
<h4> To get a var in a .properties </h4>

```properties

spring.datasource.url=${DB_NAME}

```

<h2> Maven's lifecycle </h2>

<h3> Main commands </h3>

```bash 

mvn build           # Will build

mvn verify 	    # Will build and run tests

mvn spring-boot:run # Will run the Spring Boot Application

```

<h3> Test </h3>


```bash 

# Will run every tests.
mvn test 

# Will run every tests in a class
mvn test -Dtest=ClassName

# Will run a test in a Class
mvn test -Dtest=Class#method

```

<h2> Heroku </h2>

To deploy a Java Application (Spring-boot or other) you'll need to specify the
version of Java in a system.properties file.

For Java 16 :

```properties

java.runtime.version=16

``` 


