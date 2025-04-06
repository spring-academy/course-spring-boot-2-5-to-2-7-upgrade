The base class, `WebSecurityConfigurerAdapter`, has been deprecated.

You no longer need to extend from this class. It can be replaced with an `@Bean` definition.

1.  Remove `extends WebSecurityConfigurerAdapter`.

    Let's start by opening the `SecurityConfig` class and removing the unneeded `extends`.

    ```editor:select-matching-text
    file: ~/exercises/src/main/java/example/cashcard/SecurityConfig.java
    text: "extends WebSecurityConfigurerAdapter"
    ```

    ```java
     public class SecurityConfig { ... }
    ```

2.  Delete the `configure` method.

    The `configure()` method should now indicate it is not overriding a corresponding method in the super class, which is because there is no super class anymore.

    ```java
    // DELETE the entire configure method!
     @Override
     protected void configure(HttpSecurity http) throws Exception {
         http.
            authorizeRequests((authz) ->
                authz
                    .antMatchers(new AntPathRequestMatcher("/cashcards/**")).hasRole("CARD-OWNER")
                    .antMatchers(new AntPathRequestMatcher("/h2-console/**")).permitAll()
            )
            .csrf().disable()
            .httpBasic(withDefaults());
     }
    ```

    You'll now replace the `configure` method with the corresponding `@Bean` definition.

3.  Add the `SecurityFilterChain` bean.

    The former function of the `configure` method is now handled by a
    `SecurityFilterChain` bean.

    ```java
    @Bean
    public SecurityFilterChain filterChain(HttpSecurity http) throws Exception {
    http.authorizeHttpRequests()
        .antMatchers("/cashcards/**").hasRole("CARD-OWNER")
        .antMatchers("/h2-console/**").permitAll()
        .and()
        .csrf().disable()
        .httpBasic(withDefaults());
    return http.build();
    }
    ```

    Don't forget to add the import for `SecurityFilterChain`:

    ```java
     import org.springframework.security.web.SecurityFilterChain;
    ```

    While you're at it. delete the import for `WebSecurityConfigurerAdapter`:

    ```java
    // Delete this import statement
    import org.springframework.security.config.annotation.web.configuration.WebSecurityConfigurerAdapter;
    ```

4.  **C**ompile the code

Now is a good time to **C**ompile the code again.

```dashboard:open-dashboard
name: Terminal
```

```shell
[~/exercises] $ ./mvnw clean compile
```

It still compiles, but we still have some deprecations messages in the output

```shell
...
[INFO] /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java: /course-spring-boot-2-5-to-2-7-upgrade-code/src/main/java/example/cashcard/SecurityConfig.java uses or overrides a deprecated API.
```

1. Update our notes.

Before we move on, let's note the change in the `upgrade-notes.md` file.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```

```markdown
- Replace `WebSecurityConfigurerAdapter` super class with `SecurityFilterChain` bean definition
```
