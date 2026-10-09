In a previous lab we updated the `spring-boot-starter-parent` to `2.7.x`, which resulted in a compile error. We're okay with this error for now.

Next, let's try to mitigate any hard-coded Spring dependency versions in our application.

We'll keep using the iterative **SCAR** method as we progressively upgrade our application.

## Make a **S**mall Change

1. Locate hard-coded Spring dependency versions.

   Open `pom.xml` and search through the Spring dependencies within.

   Can you find any hard-coded versions?

   ```editor:select-matching-text
   file: ~/exercises/pom.xml
   text: "spring-data-jdbc"
   before: 2
   after: 2
   ```

   Look at `spring-data-jdbc` -- it's version is hard-coded!

   ```xml
    <dependency>
       <groupId>org.springframework.data</groupId>
       <artifactId>spring-data-jdbc</artifactId>
       <version>2.2.6</version>
    </dependency>
   ```

2. Search the dependency tree.

   You can also see this version from the Maven Dependency Tree.

   In the **Terminal**, generate the dependency tree with the following command, using the `grep` command to filter for our hard-coded dependency of `spring-data-jdbc`:

   ```dashboard:open-dashboard
   name: Terminal
   ```

   ```shell
   [~/exercises] $ ./mvnw dependency:tree | grep spring-data-jdbc
   ```

   You'll see output that looks like this:

   ```shell
   [INFO] +- org.springframework.data:spring-data-jdbc:jar:2.2.6:compile
   ```

   This version is far too old for the version of Spring Boot we're targeting, which is 2.7.x.

   Let's try to fix it!

3. Comment out the `<version>` tag

   ```xml
    <dependency>
       <groupId>org.springframework.data</groupId>
       <artifactId>spring-data-jdbc</artifactId>
       <!-- comment out the explicit version -->
       <!-- <version>2.2.6</version> -->
    </dependency>
   ```

Ok, time to compile and assess.
