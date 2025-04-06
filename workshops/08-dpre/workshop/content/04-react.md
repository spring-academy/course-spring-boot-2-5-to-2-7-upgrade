Now we can fix the offending property.

Replace the key `spring.mvc.locale` with the key `spring.web.locale` as the Migrator suggested:

```editor:select-matching-text
file: ~/exercises/src/main/resources/application.yml
text: "mvc:"
```

```yaml
spring:
  web:
    locale: en_US
```

You can now re-run the application and verify you've eliminated the deprecated key.

Kill any running apps in the **Terminal** by pressing `CTRL-C`, then run the application again.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw spring-boot:run
...
2023-08-17 11:17:08.305  INFO 88094 --- [           main] example.cashcard.CashCardApplication     : Started CashCardApplication in 4.691 seconds (JVM running for 5.086)
```

Great! You've eliminated the deprecated properties.

Let's update our upgrade notes again:

```markdown
- Property `spring.mvc.locale` is deprecated
  - replaced by `spring.web.locale`
```
