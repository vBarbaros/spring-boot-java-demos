
### Ante-Thoughts

The morning commute in the big cities starts early, around 6 a.m., and follows the usual path: bus, metro, maybe another bus. It's a routine 
that tens or hundreds of thousands take part in every day, or almost. During those morning hours, we ride in all stages of alertness—from
caffeine-fueled energy to heavy-lidded drowsiness. You might see it if you looked up. But few do.

Instead, all the attention is directed towards something more important, or that’s what every one of them thinks they do. They all look into their smartphones, 
swiping from one video to the next every few seconds. That’s the reality they have chosen.

Yet just outside their screens, a harsher reality unfolds. Homelessness is no longer rare. It has no single face. It touches all walks of life. And as long as 
we, the commuters, stay absorbed in digital worlds, the struggles right outside bus window, or in front of the metro entrance, stay invisible - 
easier to ignore than to face.

### Introduction

# Introduction

Back when I was fresh out of an internship, I decided to build a small Java project. Good practices, I thought. Lots of Googling, lots of Stack Overflow.

I found a promising Spring Boot app on GitHub. Eagerly, I opened it—only to feel like Neo staring at the Matrix.

"Well," I laughed, "at least the lines go sideways. That's something!"

Java's always been about order: Classes, strict types, methods that know what they want. But here was code that looked like this:

```java
public boolean verifyComplete() {
    var fileLocation = getFileLocation();
    val fileUploaded = checkFileUploaded(fileLocation);
}
```
That var and val magic? It's real—and it’s changing how we code. Let’s dig into where they came from and what they mean for Java's future.

# The Story of `var` and `val`

## Timeline of `var`

The `var` keyword showed up fairly recently. It made its first appearance in Java SE 10 back in March 2018.

`var` lets you skip explicitly stating the type when declaring local variables. Instead, Java figures out the type for you. 
According to the official documentation, it was supposed to make your code more readable and cut down on boilerplate.

And sure, readability got a boost. But about that boilerplate? Not so much.

Here’s a classic Java snippet from the release notes:

```java
URL url = new URL("http://www.oracle.com/");
URLConnection conn = url.openConnection();
Reader reader = new BufferedReader(
   new InputStreamReader(conn.getInputStream()));
```

Now, here's the same example using var:

```java
var url = new URL("http://www.oracle.com/");
var conn = url.openConnection();
var reader = new BufferedReader(
   new InputStreamReader(conn.getInputStream()));
```
The number of lines? Still three. The logic? Still there. The only difference is that Java saves you from typing the types.

So, yes, it’s cleaner. But “less boilerplate”? That's debatable.


## Timeline of val
The story of Lombok’s val is a bit older—and more interesting.

val was introduced in Lombok version 0.10 (around October 3, 2011). It went even further than var: not only did it infer types, 
but it also made the variables immutable. Once you assign a value to a val variable, you can't reassign it later.

Fast forward ten years, and val got even stricter with enhancements like adding the final keyword automatically (in Lombok v1.18.22, released on October 7, 2021).

Ten years almost to the day. Now that's patience.



A Real-Life Analogy: Poverty, var, and val
Let’s shift gears a bit.

Sometimes, to truly understand a concept, you need a vivid example—something outside the cozy bubble of programming.

Let’s talk about poverty.

What comes to mind when you hear that word? Maybe lack of safety, poor housing, or no legal protection. These are not just abstract ideas—they're the harsh realities for millions.

In 2022, Canada's poverty rate was 9.9%, according to Stats Canada. That’s nearly four million people—about the size of Montreal or the combined population of Vancouver and Calgary.

And yet, most of us only catch glimpses of poverty through a social media reel or a YouTube documentary. It's distant, sanitized.

But real poverty? It’s messy. It’s raw. And it’s everywhere if you know where to look.


Bringing It Together: A Code Example
Let's connect this idea back to var and val.

In Java, var represents changing conditions—just like someone's safety level can fluctuate based on their environment.

Meanwhile, val represents fixed conditions—things that don't (or can’t) easily change, like a chronic lack of legal protection.

Here's a simple Java program to illustrate:

```java
import lombok.val;

public class PovertyAnalogy {
   public static void main(String[] args) {
       // 'var' represents fluctuating circumstances, including exposure to violence
       var safetyLevel = "vulnerable";
       System.out.println("Initial safety level: " + safetyLevel);
       
       safetyLevel = "witnessing domestic violence"; // A negative change in environment
       System.out.println("Exposure to violence at home: " + safetyLevel);


       safetyLevel = "living in a high-crime area"; // Another shift in risk
       System.out.println("Environment with high crime rates: " + safetyLevel);


       safetyLevel = "victim of assault"; // A direct experience of violence
       System.out.println("Experienced direct violence: " + safetyLevel);


       var housingSecurity = "precarious";
       System.out.println("Initial housing security: " + housingSecurity);


       housingSecurity = "evicted and unsafe"; // Housing loss leading to increased vulnerability
       System.out.println("Homeless and facing increased danger: " + housingSecurity);


       // 'val' represents fixed states of deprivation that can increase vulnerability to violence
       val lackOfBasicSecurity = true; // Persistent lack of safety nets
       System.out.println("Consistent lack of basic security: " + lackOfBasicSecurity);


       val limitedLegalRecourse = true; // A fixed barrier to seeking protection
       System.out.println("Restricted access to legal help: " + limitedLegalRecourse);
      
       // Illustrating how a fixed state ('val') can make a fluctuating state ('var') worse
       if (lackOfBasicSecurity) {
           safetyLevel = "extremely vulnerable"; // Lack of security amplifies the risk
           System.out.println("Lack of security exacerbates vulnerability: " + safetyLevel);
       }
   }
}
```
Here, var allows changes, just like life circumstances can change. But val locks in a disadvantage—making already tough situations even tougher.

## Final Thoughts
By blending real-world analogies with Java code, we can not only understand programming better but also stay connected to the world around us.

Next time you see a var or val in code, maybe you’ll think a little differently—not just about types, but about change, about immutability, 
and about the invisible struggles many face every day.


### References
[1] [Types of Variable in Java - Oracle Documentation](https://docs.oracle.com/javase/tutorial/java/nutsandbolts/variables.html)

[2] [var identifier introduced in JDK 10](https://docs.oracle.com/javase/10/language/toc.htm#JSLAN-GUID-7D5FDD65-ACE4-4B3C-80F4-CC01CBD211A4)

[3] [Project Lombok val - local variable declaration](https://projectlombok.org/features/val)

[4] [val was introduced in lombok 0.10](https://mvnrepository.com/artifact/org.projectlombok/lombok/0.10.1)

[5] [NEW in Lombok 1.18.22: val gets replaced with final var.](https://mvnrepository.com/artifact/org.projectlombok/lombok/1.18.22)

[6] [SpringBoot - Using @Value annotation](https://docs.spring.io/spring-framework/reference/core/beans/annotation-config/value-annotations.html)

[7] [Stats Canada - Poverty line](https://www.statcan.gc.ca/en/topics-start/poverty)

[8] [Canada population - 2022](https://www150.statcan.gc.ca/n1/daily-quotidien/230322/dq230322f-eng.htm)

[9] [Canadian cities - population](https://en.wikipedia.org/wiki/List_of_the_largest_population_centres_in_Canada)