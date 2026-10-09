The `HttpSecurity` class has replaced the deprecated `antMatchers`, `mvcMatchers` and `regexMatchers` with an expanded `requestMatchers` method.

It can usually introspect the type of matcher by just specifying a String path value. However, this will depend on which dependencies are currently on your classpath. You can pass in a direct `RequestMatcher` instance to ensure the correct one is applied.

1. Fix the `.antMatchers()`.

   Open `SecurityConfig.java` again and replace the `.antMatchers()` calls with the following `requestMatchers()` calls:

   ```editor:select-matching-text
   file: ~/exercises/src/main/java/example/cashcard/SecurityConfig.java
   text: "antMatchers"
   ```

   ```java
   // Delete these antMatchers
   // .antMatchers("/cashcards/**").hasRole("CARD-OWNER")
   // .antMatchers("/h2-console/**").permitAll()

   // replace with these requestMatchers
   .requestMatchers(new AntPathRequestMatcher("/cashcards/**")).hasRole("CARD-OWNER")
   .requestMatchers(new AntPathRequestMatcher("/h2-console/**")).permitAll()
   ```

1. **C**ompile the code

   Now is a good time to **C**ompile the code again.

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw clean compile
   ```

   It still compiles, but we **_still_** have some deprecations messages in the output

   ```shell
   [INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
   ```

1. Update our notes.

   Before we move on, let's note the change in the `upgrade-notes.md` file.

   ```editor:open-file
   file: ~/exercises/upgrade-notes.md
   ```

   ```markdown
   - Replace `antMatcher` with `requestMatcher` builder method
   ```

Let's move on to the next deprecations.
