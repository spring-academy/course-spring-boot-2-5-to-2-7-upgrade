Open `pom.xml` and find the `assertj-core` dependency.

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "assertj-core"
```

```xml
<dependency>
    <groupId>org.assertj</groupId>
    <artifactId>assertj-core</artifactId>
    <version>3.24.2</version>
    <scope>test</scope>
</dependency>
```

You'll notice the version of `assertj-core` has been explicitly included. Spring Boot, specifically the `spring-boot-starter-test` dependency will manage the version of this library for you.

1. Make a **S**mall Change

   First, check the version of `assertj-core` with the Maven Dependency Tree plugin:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep assertj-core
   ```

   You should see the following output:

   ```shell
   [INFO] \- org.assertj:assertj-core:jar:3.24.2:test
   ```

   You can now comment out line the `version` for `assertj` in the `pom.xml`.

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "assertj-core"
   ```

   ```xml
   <dependency>
       <groupId>org.assertj</groupId>
       <artifactId>assertj-core</artifactId>
       <!-- <version>3.24.2</version> -->
       <scope>test</scope>
   </dependency>
   ```

1. Check the dependency tree again.

   Now, check the version of `assertj-core` with the Maven Dependency Tree plugin again:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep assertj-core
   ```

   You should see the following output:

   ```shell
   [INFO] \- org.assertj:assertj-core:jar:3.22.0:test
   ```

Hmm, the output is similar, but it's actually _older than the explicit version_ that was previously set: `3.24.0` instead of `3.24.2`.

Why is this?

### Learning moment: newer isn't always better

The Spring Boot maintainers endeavor to ensure that all managed versions are compatible with the components of the frameworks. This might be an older version of a dependency.

Not knowing exactly why this version was explicitly included, you still want to verify this change will not adversely affect the tests.
