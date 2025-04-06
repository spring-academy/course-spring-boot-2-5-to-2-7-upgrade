Don't forget, you want to disable or remove the `spring-boot-properties-migrator` before running this application in production.

The choice is yours, or perhaps your organization's policy, to either delete the dependency or just comment it out for use during future Spring Boot upgrades.

```editor:select-matching-text
file: ~/exercises/pom.xml
text: "spring-boot-properties-migrator"
```

```xml
<!-- comment out or delete -->
<!-- <dependency> -->
    <!-- <groupId>org.springframework.boot</groupId> -->
    <!-- <artifactId>spring-boot-properties-migrator</artifactId> -->
    <!-- <scope>runtime</scope> -->
<!-- </dependency> -->
```
