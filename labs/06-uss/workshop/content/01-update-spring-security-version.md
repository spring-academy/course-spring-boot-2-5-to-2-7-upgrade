Spring Security is currently being managed by the Spring Boot Parent. You'll see the Spring Security starter in the `pom.xml` defined like:

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "spring-boot-starter-security"
before: 2
after: 1
```

```xml
<dependency>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-starter-security</artifactId>
</dependency>
```

Currently, however, this Spring Dependencies is tracking the latest Spring Security `5.7.x` release. You can verify this with the Maven Dependency Tree plugin:

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep spring-security
[INFO] |  +- org.springframework.security:spring-security-config:jar:5.7.10:compile
[INFO] |  |  \- org.springframework.security:spring-security-core:jar:5.7.10:compile
[INFO] |  |     \- org.springframework.security:spring-security-crypto:jar:5.7.10:compile
[INFO] |  \- org.springframework.security:spring-security-web:jar:5.7.10:compile
```

Notice that the Spring Security Version is set to `5.7.10`.

To prepare for Spring Security 6 you'll need to update the Spring Security version to follow the `5.8.x` release. This can be accomplished by overriding the Spring Security version placeholder established by the Spring Boot parent.

Let's run through an entire **SCAR** pass to update our Spring Security version.

## Make a **S**mall Change

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "<properties>"
before: 0
after: 3
```

Add the Spring Security version property:

```xml
<properties>
	<java.version>1.8</java.version>
	<itextpdf.version>5.5.13.3</itextpdf.version>
    <!-- add the property below -->
	<spring-security.version>5.8.5</spring-security.version>
</properties>
```

You are utilize the same feature we previously discussed regarding moving versions to Maven Properties.

In this case, however, `spring-security.version` _has already been established by the Spring Boot Parent_ and you are free to override it here, locally, in your own `pom.xml` file. Maven will use this property to override the one previously set by the Spring Boot Parent.

That was truly a **S**mall Change. Let's compile and see the impact.

## **C**ompile the code

Now **C**ompile the code. You should see some interesting output.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw clean compile
...
[INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
[INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: Recompile with -Xlint:deprecation for details.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```

The code _does_ compile successfully, but you should see some **deprecation messages**. For example, `... SecurityConfig.java uses or overrides a deprecated API`.

Before we deal with those deprecations, we should verify that we _are_, in fact, using Spring Security 5.8.x.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep spring-security
```

You should see the following output:

```shell
[INFO] |  +- org.springframework.security:spring-security-config:jar:5.8.5:compile
[INFO] |  |  \- org.springframework.security:spring-security-core:jar:5.8.5:compile
[INFO] |  |     \- org.springframework.security:spring-security-crypto:jar:5.8.5:compile
[INFO] |  \- org.springframework.security:spring-security-web:jar:5.8.5:compile
```

Great! Now let's go deal with deprecations.

## **A**ssess the results

Take a look at that compile output again:

```shell
[INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
[INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: Recompile with -Xlint:deprecation for details.
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
```

### Update our notes.

Add a new section for the security upgrade `Upgrade Spring Security Version` to our `upgrade-notes.md` file.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

```markdown
### Upgrade Spring Security Version

- Upgrade Spring Security to `5.8.5`
- Spring Security deprecations
  - [INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
  - [INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java
  - Reference: https://docs.spring.io/spring-security/reference/5.8/migration/index.html
```

## **R**eact to the error output

Most modern IDE's will let you know if you're interacting with a deprecated class or method. Let's address these deprecations.

The SCAR method has always been an iterative process. It is especially an iterative process now even more so.
