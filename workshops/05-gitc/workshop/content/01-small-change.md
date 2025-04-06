We need to fix the code that references the deprecated method that is no longer present in Spring Boot 2.7.x.

Let's go for it!

## Make a **S**mall change

1. Locate the error.

   According to the stack trace we see when we attempt to compile, the `CashCardApplication` cannot compile.

   It looks like the problem is related to a constructor for an `ApplicationStartingEvent`:

   ```shell
   [ERROR] /home/eduk8s/exercises/src/main/java/example/cashcard/CashCardApplication.java:[50,17] constructor ApplicationStartingEvent in class org.springframework.boot.context.event.ApplicationStartingEvent cannot be applied to given types;
   ```

2. Understand the problem.

   Open `src/main/java/example/cashcard/CashCardApplication.java` and look at the problematic constructor.

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/CashCardApplication.java
   text: "@Deprecated"
   after: 6
   ```

   What do you notice?

   ```java
   @Deprecated
   public MyApplicationStartingEvent(SpringApplication application, String[] args) {
       super(application, args); // <== Compile error here!

       log.warn("My parent is deprecated!");

   }
   ```

   You'll see that the `super` method signature is no longer valid. Let's fix it!

3. Update the broken constructor.

   A bit of research into the deprecated method signature tells us that we need to support a `ConfigurableBootstrapContext` argument.

   Update `MyApplicationStartingEvent` to support this new arguments and remove the `@Deprecated` annotation. Be sure to add the new `import` statement:

   ```java
   import org.springframework.boot.ConfigurableBootstrapContext;
   ...
   // @Deprecated <== Delete this annotation.
   public MyApplicationStartingEvent(ConfigurableBootstrapContext bootstrapContext, SpringApplication application, String[] args) {
       super(bootstrapContext, application, args);
       ...
   }
   ```

   This error should be fixed.

   Now let's fix any references to this constructor.

4. Fix and find references to the broken constructor.

   In the Editor, search the codebase for references to the `MyApplicationStartingEvent` constructors.

   You'll find it's references in the same `CashCardApplication` class:

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/CashCardApplication.java
   text: "myApplicationListener.onApplicationEvent"
   before: 0
   after: 0
   ```

   ```java
   public static void main(String[] args) {
       ...
       // This is broken now!
       myApplicationListener.onApplicationEvent(new MyApplicationStartingEvent(springApplication, args));
       ...
    }
   ```

   Fix the constructor call by passing in a `new DefaultBootstrapContext()`, making sure to add the new import statement:

   ```java
   import org.springframework.boot.DefaultBootstrapContext;
   ...
   public static void main(String[] args) {
       ...
       // Fixed!
       myApplicationListener.onApplicationEvent(new MyApplicationStartingEvent(new DefaultBootstrapContext(), springApplication, args));
       ...
   }
   ```

Feels good to write some code, right? Now let's compile and see if we fixed the issue.
