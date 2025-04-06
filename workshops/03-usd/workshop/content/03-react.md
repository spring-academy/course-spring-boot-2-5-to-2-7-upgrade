As with a previous lab, our only **r**eaction is to document the current state of the application and the actions we've taken so far.

1. Clean up the unneeded `<version>`.

   We've proven that Spring is managing the `spring-data-jdbc`dependency.

   Let's delete the commented-out `<version>` tag.

   ```xml
   <dependency>
      <groupId>org.springframework.data</groupId>
      <artifactId>spring-data-jdbc</artifactId>
   </dependency>
   ```

1. Update our notes.

   Add the following to the `Upgrade Spring Boot Parent Version` section to our `upgrade-notes.md" file:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   ## Remove hard-coded Spring/Spring Boot Dependencies

   - remove hardcoded `spring-data-jdbc` version
   ```

   With that, we're done fixing Spring managed dependencies!
