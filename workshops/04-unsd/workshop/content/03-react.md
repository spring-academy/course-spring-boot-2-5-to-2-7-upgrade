We were pleasantly surprised that Spring is managing `lombok` for us.

1. Clean up the unneeded `<version>`.

   Let's delete the commented-out `<version>` for `lombok`:

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "<version>1.18.22</version>"
   ```

   ```xml
   <dependency>
       <groupId>org.projectlombok</groupId>
       <artifactId>lombok</artifactId>
   </dependency>
   ```

1. Update our notes.

   As we have in previous labs, add the following to the `Upgrade Spring Boot Parent Version` section:

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   ## Update Non Spring/Spring Boot Managed Dependencies

   - remove hardcoded `lombok` version
   ```
