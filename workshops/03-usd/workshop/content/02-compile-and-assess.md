Now that we've commented-out all hard-coded Spring dependency versions in our `pom.xml`, let's continue with **SCAR**.

## **C**ompile the code

We've already documented in our `upgrade-notes.md` file that our code does not compile.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

But, it is a good idea to make sure that the application's state has not changed since the last baseline:

```shell
[~/exercises] $ ./mvnw clean compile
...
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  1.722 s
[INFO] Finished at: 2023-08-21T20:43:34Z
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-compiler-plugin:3.10.1:compile (default-compile) on project family-cash-cards: Compilation failure
...
```

You can, however, **A**ssess the change you just made.

## **A**ssess the `<version>` change

Run the `dependency:tree` goal again and note how the output changed.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep spring-data-jdbc
```

You'll see output that looks like this:

```shell
[INFO] +- org.springframework.data:spring-data-jdbc:jar:2.4.14:compile
```

That's better! The version is now `2.4.14` instead of `2.2.6`

The Spring Boot Parent is now managing that dependency for us, and it should remain up to date with whatever version the parent deems necessary to include that dependency.

Thanks, Spring Boot Parent!
