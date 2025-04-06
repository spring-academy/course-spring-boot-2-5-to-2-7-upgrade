We found at least one hard-coded _non_-Spring dependency. Are there any others? Let's keep looking through the `pom.xml` and find out.

1. Keep searching through `pom.xml`.

   Open up `pom.xml` and see if there are any other hard-coded non-Spring dependencies.

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "com.itextpdf"
   before: 1
   after: 3
   ```

   Look at the `itextpdf` dependency, its version is explicitly stated!

   ```xml
   <dependency>
       <groupId>com.itextpdf</groupId>
       <artifactId>itextpdf</artifactId>
       <version>5.5.13.3</version>
   </dependency>
   ```

   Let's see if Spring will manage this one for us, too.

2. Comment out the explicit `itextpdf` version and **A**ssess.

   ```xml
   ...
   <artifactId>itextpdf</artifactId>
   <!-- <version>5.5.13.3</version> -->
   ...
   ```

   Let's **A**ssess by seeing what the dependency tree says:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
    [~/exercises] $ ./mvnw dependency:tree | grep itextpdf

    [ERROR] 'dependencies.dependency.version' for com.itextpdf:itextpdf:jar is missing. @ line 76, column 15
    [ERROR]     'dependencies.dependency.version' for com.itextpdf:itextpdf:jar is missing. @ line 76, column 15
   ```

   Oh no! We're getting errors about a missing `itextpdf` JAR file. It looks like Spring is not going to manage this one for us.

Let's implement the best practice of using Maven Properties to centrally manage this dependency's version.
