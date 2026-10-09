At this point, you've reconfigured Spring Security for Spring Boot 2.7.x, and set up for the eventual jump to Spring Boot 3.1.x. Now is the time to make sure everything is still working correctly. Go ahead and run the tests.

1. Compile the code.

   If all went as planned, we should no longer have the deprecation warnings we introduced by upgrading Spring Security:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw compile
   ...
   [INFO] ------------------------------------------------------------------------
   [INFO] BUILD SUCCESS
   [INFO] ------------------------------------------------------------------------
   [INFO] Total time:  1.308 s
   [INFO] Finished at: 2023-08-21T22:02:43Z
   [INFO] ------------------------------------------------------------------------
   ```

   Nice! We have our new baseline.

1. Update our notes.

   Let's record our result in the `upgrade-notes.md` file.

   Add a line in the `Upgrade Spring Security Version` section:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   _Result:_ code compiles without errors or warnings
   ```

We did it!
