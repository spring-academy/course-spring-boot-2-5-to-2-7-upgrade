Let's see if everything still works with this older, Spring-maintained version of `assertj`.

1. **C**ompile the code.

   Actually, we'll run the tests, which does compile the code first.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean test
   ```

   Great! All the tests still pass, even with the older Spring-maintained version of `assertj`.

   ```shell
   [INFO]
   [INFO] Results:
   [INFO]
   [INFO] Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
   [INFO]
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   ```

1. **A**ssess the results.

   You are able to let the framework manage one more dependency version for you.

That's one less thing to worry about!
