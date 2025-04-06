## **A**ssess the property change

There is really nothing to **A**ssess here. There was no change in version, it was only moved to a clearer section of the `pom.xml`

Just to be sure, though, let's check the dependency tree again:
Run the `dependency:tree` goal again and not how the output changed.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw dependency:tree | grep itextpdf
```

You'll see output that version is as it was before:

```shell
[INFO] +- com.itextpdf:itextpdf:jar:5.5.13.3:compile
```

Nice! The version is the same, just managed with a property.
