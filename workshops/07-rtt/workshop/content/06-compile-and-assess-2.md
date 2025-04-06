Now that we've completely removed `assertj` in our `pom.xml`, will our app still work?

1. **C**ompile the code, take 2.

   Go ahead and compile the code, once again.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ```

   Great! Everything still compiles

   ```shell
   [INFO] Changes detected - recompiling the module!
   [INFO] Compiling 5 source files to /course-spring-boot-2-5-to-2-7-upgrade-code/target/classes
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   ```

1. **A**ssess the results, take 2.

   Now you can run the tests again to see if all the tests are still passing.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw test
   ...
   [INFO]
   [INFO] Results:
   [INFO]
   [INFO] Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
   [INFO]
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   ```

Another success! All our tests are still passing.
