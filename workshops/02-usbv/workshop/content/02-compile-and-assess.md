We've made our **S**mall Change. Now let's **C**ompile and **A**ssess!

## **C**ompile the code

Now **C**ompile the code, but as we discussed in the lesson we're going to skip running the tests for now. Don't worry, we'll have a whole set of lessons and labs dedicated to addressing any testing issues we might introduce.

Open the **Terminal** and compile, skipping the tests:

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw compile
```

So, what happened?

## **A**ssess the results

Now we can answer the same questions outlined in the first lab:

- Did you code compile?

Take a look at the output and decide for yourself. You should see error output like the following:

```shell
[INFO] -------------------------------------------------------------
[ERROR] COMPILATION ERROR :
[INFO] -------------------------------------------------------------
[ERROR] /home/eduk8s/exercises/src/main/java/example/cashcard/CashCardApplication.java:[50,17] constructor ApplicationStartingEvent in class org.springframework.boot.context.event.ApplicationStartingEvent cannot be applied to given types;
   required: org.springframework.boot.ConfigurableBootstrapContext,org.springframework.boot.SpringApplication,java.lang.String[]
   found: org.springframework.boot.SpringApplication,java.lang.String[]
   reason: actual and formal argument lists differ in length
[INFO] 1 error
[INFO] -------------------------------------------------------------
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.264 s
[INFO] Finished at: 2023-08-15T17:49:33Z
[INFO] ------------------------------------------------------------------------
```

**NOTE:** Spring Boot 2.7.x removed a method signature that was previously deprecated in Spring Boot 2.4. You can expect items deprecated in Spring Boot x.y to be removed in Spring Boot X.y+2.

So did it compile? **_NO!_**

What should we do about this right now?
