With any luck we only need to make one change: updating the `spring-boot-starter-parent` version in our `pom.xml`.

To reinforce the **SCAR** method, you'll make a series of **S**mall changes and you'll continually be **C**ompiling, **A**ssessing, and **R**eacting to the output you see.

**_Note:_** At the time of this writing, the current Spring Boot 2.7.x version is `2.7.14`.

## Make a **S**mall Change.

The first **S**mall change consists of updating the Spring Boot Parent Starter version.

The current `pom.xml` looks like this:

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "spring-boot-starter-parent"
before: 2
after: 3
```

```xml
<parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.5.6</version> <!-- <=== Update this! -->
      <relativePath/> <!-- lookup parent from repository -->
</parent>
```

The updated `pom.xml` should look like this:

```xml
<parent>
      <groupId>org.springframework.boot</groupId>
      <artifactId>spring-boot-starter-parent</artifactId>
      <version>2.7.14</version> <!-- <=== Updated! -->
      <relativePath/> <!-- lookup parent from repository -->
</parent>
```

Well that was easy! Now let's compile.
