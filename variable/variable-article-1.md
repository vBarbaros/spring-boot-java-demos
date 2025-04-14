### On variables and their many names in Java and programming at large

I was in my first week of an internship. I opened a few files from the Spring Boot app
I was about to make changes to and was petrified. I was expecting to see Java code - 
simple, strongly typed, javadoc enhanced commented Java code. What I was facing was more of
those lines of cryptic code we saw Neo reading in Matrix, with the only difference that
the lines where still horizontal. "That's already good", I thought, "...horizontal lines means 
it's not entirely alien. I can read that, assuming it's still written from left to right..." 

There is a reason that over the last few decades, generations of programmers have been introduced
to coding through Java. Java has Classes, Classes has data and behaviour. Each data type 
is clearly defined, using strict keywords and order. The class' behaviour, aka method, 
knows very well what input data type it expects and what the output type will be.

Now, imagine my surprise when I saw this code ():
```java
var fileLocation = getFileLocation();
val fileUploaded = checkFileUploaded(fileLocation);
```
My first reaction was "No, Java was hacked by a JavaScript ninja (or NinjaScript)!!!"



#-------------------------------------


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
full 10 years period, almost day by day.

This feature is advertised in lombok, as hassle-free final local variables. Fair enough, it's indeed 
hassle-free, when you consider that instead of `final int` we'll need to go only with `val`. Nevertheless, 
using `val` is not entirely hassle-free, is it?

Consider the following situation. You start working with some legacy code, and you go into one method
and see some `var` instantiated variables. They are local variables so we may try to update it somewhere below.
We'll do the same with a `val` variable defined in the same method, as a local variable. 

Now, here is the question - which one will fail to be updated? Also, will it fail at compile or runtime?

It may be confusing, but I'll offer here an exmplae that will stick to your memory forever. And I'll do that 
by using an example that will bring us out of our IT bubble, in which we spend most of our lives.

We'll use as an example, some concepts from `Poverty`. Yes, a real, socially debilitating phenomenon, and 
not a witty Java API with a weird name. So, let's proceed.

What comes to your mind when you hear the word poverty? I won't ask you `when you see poverty` because this
is not something everyone sees it. Most of us are so isolated socially, and so wrapped up into our own 
social media apps' feeds, that the only place we may see `poverty` may happen on a random YouTube reel or
in a last-fad mini series we binge until past midnight. I really mean the real poverty from the actual real life.

So, I'll repeat my question - what comes to mind when you hear the word `poverty`?

Here's what comes to my mind when I hear this word - `lack of safety`, `bad housing or lack thereof`, 
`lack of legal or even basic security`. These are some pretty nasty combinations of words that most of you 
have not heard of, or maybe sporadically read about in a dictionary, but according to Stats Canada, in 2022
the poverty rate was 9.9%; not sure why it is called rate, because according to those same documents, the 
same percentage needs to be interpreted as the actual percentage of the population. In 2022 Canada's population 
was 39,566,248 ppl, thus 9.9% is roughly 3,917,059 ppl. This represents entire city of Montreal, or roughly
Vancouver and Calgary put together (of course this'll never happen, but just imagine).

Now, what does poverty has with all these not-so-sexy numbers from Stats Canada?

You see, when we want to memorize a concept nad we want that memory to stay with us for long, the best 
way to achieve this is to use some vivid examples. Of course, we could pick many vivid examples around us,
but those will not be that useful. You may ask how these are any useful to us, those who can afford 
to read from and write unto a PC? It's a good questions.

My answer is the following - many problems in our society are not solved, or are persistently ignored
because the main streams of information are ignoring them. 

By reading this article, you may learn something about Java and lombok features, but you'll also learn 
something that is part of our real life, as well. Next time you take a walk in a less favorable area of
your city, your mind will, hopefully, not wander about the latest TikTok video on how to spell banana 
backward, but it'll spot some faces, out of the stats I just gave you above.

```java
import lombok.val;

public class PovertyViolenceAnalogy {
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