Now that the application is compiling and all tests are passing, we're ready to begin run-time testing of the application. The first step on the path to "Running" the application is to verify that we've remediated any deprecated properties. To facilitate that, the Spring team created a utility called the "Spring Boot Properties Migrator".

In this lesson we'll learn how to use this utility to help us find and remediate deprecated properties. We'll need to perform the following steps:

1. Add the Spring Boot Properties Migrator to our POM.
2. Run the application.
3. Fix any identified errors.
4. Once completed, we'll remove it from our POM, as it's not intended to be a permanent addition.

@@@alert
{
"text": "#### Note \n
During \"Assess\" we modified the logging subsystem to use `INFO` logging. During this phase you may need to adjust your logging to `DEBUG` in order to get the necessary information to make informed reactions.",
"type": "info"
}
@@@

## Spring Boot Properties Migrator

Let's add the utility to our POM file and run the application.

1. Add Spring Boot Properties Migrator to the POM. Open the POM and add the following to the dependencies section at the top.

   ```xml
   <dependency>
       <groupId>org.springframework.boot</groupId>
       <artifactId>spring-boot-properties-migrator</artifactId>
       <scope>runtime</scope>
   </dependency>
   ```

2. Run the application

   ```shell
   $ ./mvnw spring-boot:run [required parameters]
   ```

   The `[required parameters]` in the above command would be any parameters or properties required by your application for it to successfully bootstrap and run.

3. **Assess** the results by reviewing the console log and/or any log files produced by the application.
   1. Did the application successfully bootstrap and run?
      1. If YES, move to step 4.
      2. If NO, what happened? The output from the utility will guide you in the right direction. You might also see "Class Format" errors. Fix and repeat. Please take a look at our more detailed instructions in the **Spring Boot Migrator output** section regarding both of these errors, later in this lesson.
4. Comment out the Properties Migrator Dependency from the Project POM.

@@@alert
{
"text": "Notice that we state to _comment out_ the Spring Boot Properties Migrator. A utility like this will have use when the application is upgraded over time. It's recommended to leave this entry in the POM, however, it should be commented out and should **NOT** be run in Production.\n\nUltimately, you need to follow the accepted practices established by your team and operating environment. So, if commented code is frowned upon, just remove the dependency completely.",
"type": "info"
}
@@@

### Spring Boot Property Migrator Output

Errors produced by the Properties Migrator will look something like this.

```shell
The use of configuration keys that have been renamed was found in the environment:

Property source 'Config resource 'class path resource [application.yml]' via location 'optional:classpath:/'':
        Key: spring.artemis.host
                Line: 11
                Replacement: spring.artemis.broker-url

Each configuration key has been temporarily mapped to its replacement for your convenience. To silence this warning, please update your configuration to use the new keys.
```

In the example output above, the Properties Migrator has highlighted that we're using a Deprecated property named `spring.artemis.host`. Further, it's identified the File and Line # where this property can be found, as well as the appropriate property to be used: `spring.artemis.broker-url`.

Using the **SCAR** method, we'd fix this property in the `application.yml` and attempt running the application again. Then we'd once again "Assess" the results and "React". We'd repeat this process until all Property Migrator errors and warnings have been resolved.

If you received other runtime errors or warnings, you should deal with those the same way you dealt with them during the Update/Compile process. At this point, errors are likely related to configuration and or "Class Format".

### Resolving Class Format Errors

These errors will be dealt with by finding the correct version of the library and specifying it in our POM.

You could do this by specifying a specific version. This might be a case where you need to _downgrade_ a library to work with your application.

In the case of transitive dependency conflict, you might create an "exclusion", then making the required library a direct dependency of our project. For more details on this process see [Maven Dependencies](https://maven.apache.org/guides/introduction/introduction-to-dependency-mechanism.html) and [Dependency Exclusions](https://maven.apache.org/guides/introduction/introduction-to-optional-and-excludes-dependencies.html#dependency-exclusions).

At this point you should've dealt with all property deprecations and runtime errors. Your application should be successfully bootstrapping and running.

@@@alert
{
"text": "Class Format Errors typically only surface when you aren't on the latest GA version of Java. We've highlighted them here because some dependent libraries your project uses could've updated their code and compiled against a new Java version, while your application is compiled against an older version of Java.",
"type": "warning"
}
@@@

## Establish a New Baseline

Document the current state in writing and in source control.

1. Take note of any errors, warnings, or issues in the "Upgrade-Notes.md"
   1. Append a new heading to the document titled - "Deprecated Properties".
   2. Document any remaining warnings or other known issues.
2. Issue a commit.
