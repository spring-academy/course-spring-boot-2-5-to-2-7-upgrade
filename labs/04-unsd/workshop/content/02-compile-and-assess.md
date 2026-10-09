Now that we've commented-out `lombok`'s hard-coded version in our `pom.xml`, let's continue with **SCAR**.

## **C**ompile the code

Well, this is familiar. We already know that our application does not compile, and should have the same error messages as in the previous lab.

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

Feel free to review our the our upgrade notes as a reminder if needed.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

But, we can **A**ssess!

## **A**ssess the version change

Run the `dependency:tree` goal again and not how the output changed.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep lombok
```

You'll see output that looks like this:

```shell
[INFO] +- org.projectlombok:lombok:jar:1.18.28:compile
```

That's _much_ better. The version is now the newer `1.18.28` rather than the older `1.18.22`.

Lombok is a widely used project and the Spring Maintainers have provided dependency management for it. Thanks for managing that for us, Spring!
