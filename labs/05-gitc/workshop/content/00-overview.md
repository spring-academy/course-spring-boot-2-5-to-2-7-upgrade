As we're well aware, our application does not currently compile. We're finally ready to fix it!

We have to address the deprecated code that was present in Spring Boot 2.5 but removed in Spring Boot 2.7.x. Our application must use this deprecated code somewhere!

Here is a refresher on the output we saw in the first module of this lab:

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

As always, we'll follow the **SCAR** method to fix this problem.

## Review our Upgrade Notes

Before we begin, remember that we're keeping detailed notes of the baseline state of our application as we upgrade it. Take a look at `upgrade-notes.md` to review where we are now.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```
