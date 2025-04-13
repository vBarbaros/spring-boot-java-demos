### On variables and their many names in Java and programming at large

When you are just getting started as a programmer, there are many things you encounter 
that don't make total sense, initially. You hear your teammates using the words variable 
and value interchangeably. You see same variable being declaring in different places, and 
then you need to call it local, or static, or that thingy that stores that thing... Uhhh...

On top of that, we now have lombok, which allows us to simplify our code even more, and 
reduce the definition of our variable to var, or val, or... wait, which one is which, again?

Oh, right. Not to forget that if we work in Spring Framework, our Java code becomes really 
not that Java-ish. We have annotations! Here is one of them - @Value

As we can see, there are many ways we can define, instantiate, and get hold of values in our 
Java / Spring Boot application.

Today we'll sort out what are the `val` and `var` identifiers or types (we'll find out
which one is which, as well), and will walk through an exhaustive and complete set of examples.
Finally, we'll consider some common pitfalls we may encounter, when using one or the other.

### The timeline of `var` and `val`

The var identifier comes from Java, and according to the official documentation it was introduced 
in Java 10, which happened to be March 2018. The var identifier allows for type inference when 
declaring local variables. In the official documentation it is stated that this inference type 
was meant to make your Java code morea readable and reduce the amount of the required boilerplate code.
While I do agree that the former was achieved, the latter is not really.

Consider for yourself, based on the example from the same official release notes, we have two cases.
First one shows the code snippet with classic Java code, which consists of 3 lines of code:

```java
URL url = new URL("http://www.oracle.com/"); 
URLConnection conn = url.openConnection(); 
Reader reader = new BufferedReader(
    new InputStreamReader(conn.getInputStream()));
```
Now, let's see what `var` does to the code, when replacing the types:
```java
var url = new URL("http://www.oracle.com/"); 
var conn = url.openConnection(); 
var reader = new BufferedReader(
    new InputStreamReader(conn.getInputStream()));
```

It definitely made it more readable, but did it reduce the boilerplate code? Hardly so, since we still 
have 3 lines of code, and we still have the same statements in each line. The only difference is that the
variable type is missing on the declaration side.

Ok, let's proceed further. The lombok's `val` type was first released in lombok version 0.10 (according to 
maven repository, the release dates from October 03rd, 2011). It was further enhanced with the final 
keyword much later, in lombok version 1.18.22, which is dated from October 7th, 2021. This represents a
full 10 year period, almost day to day.



### References
[1] [Types of Variable in Java - Oracle Documentation](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html)

[2] [var identifier introduced in JDK 10](https://docs.oracle.com/javase/10/language/toc.htm#JSLAN-GUID-7D5FDD65-ACE4-4B3C-80F4-CC01CBD211A4)

[3] [Project Lombok val - local variable declaration](https://projectlombok.org/features/val)

[4] [val was introduced in lombok 0.10](https://mvnrepository.com/artifact/org.projectlombok/lombok/0.10.1)

[5] [NEW in Lombok 1.18.22: val gets replaced with final var.](https://mvnrepository.com/artifact/org.projectlombok/lombok/1.18.22)

[6] [SpringBoot - Using @Value annotation](https://docs.spring.io/spring-framework/reference/core/beans/annotation-config/value-annotations.html)