# Spring Boot notes

Opinionated Java framework for stand-alone production apps. Still need to use Spring, but boot helps you.

* Hibernate - ORM
* Struts – MVC
* Spring
	* AOP (Cross cutting – Logging, security, caching etc): decouple ccc from the objects they affect, DI


Model: POJO – just data (MVC) – usually linked to what you display in frontend
Entity: Class corresponds to table and instance to a row (ORM)
*	They are similar 

Run unit tests: 
```
./gradlew clean test
```
Run app:
```
./gradlew bootRun
```
Build app (./gradlew if have a wrapper):
```
gradle build
```

After adding new dependency, running ```gradle build``` will download

## Spring Autowiring – Dependancy Injection
*	Spring IOC Container – creates beans that are needed
*	Let spring newup the dependency – instead of passing in
*	Provides the bean to the class and manage it
*	For class to be managed by spring – put ```@Component``` annotation
*	If have 2 or more implementations, could name variable as implementation name - use ```@Qualifier``` or put them in separate packages

```
@Component
class HelloService {

public class Example {
   @Autowired
   HelloService service; 
```

```@Component```	│ generic stereotype for any Spring-managed component (Could use for everything, but following annotations provides better processing by tools and associations with aspects)

* ```@Repository```	│ stereotype for persistence layer                   
* ```@Service```   	│ stereotype for service layer                      
* ```@Controller```	│ stereotype for presentation layer (spring-mvc)    

```@EnableScheduling``` Allows you to put @Scheduled(fixedRate=1000) annotations to create repeating actions

## Useful links
Rest Web Services With Spring Boot](https://www.youtube.com/watch?v=YEEUn5JZ9t0)
[IntelliJ IDEA Spring Boot Gradle Tutorial](https://www.youtube.com/watch?v=Cuz_mnrWXnk)
[Sprint Boot and MongoDb CRUD](https://www.codementor.io/gtommee97/rest-api-java-spring-boot-and-mongodb-j7nluip8d)

## Unit testing
**Mock** Just test that something was called - observation point when we need to do Behavior Verification
**Stub** Just returns predefined data. When something, return something
**Fake** working implementation (e.g. in memory db), but different to production.

# Other info
Multiple java files without gradle / maven:
```
javac –cp Lombok.jar Mountain.java
```
