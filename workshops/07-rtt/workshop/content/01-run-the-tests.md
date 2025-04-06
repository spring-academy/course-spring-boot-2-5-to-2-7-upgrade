Now is a good time to run all the tests!

1. Run the tests.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw test
   ```

   All of the code should compile and the tests should pass at this point.

   ```shell
   [INFO] Results:
   [INFO]
   [INFO] Tests run: 19, Failures: 0, Errors: 0, Skipped: 0
   [INFO]
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   ```

   They pass!

   For the first time since upgrading to Spring Boot 2.7 we have 0 failures, 0 errors, and 0 skipped tests.

1. Update our upgrade notes.

   Add a new section in the upgrade notes titled `Test - Initial Test Execution`:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   ## Test - Initial Test Execution

   _Result:_ code compiles without errors or warnings and all tests pass
   ```
