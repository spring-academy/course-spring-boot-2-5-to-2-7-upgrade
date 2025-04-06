Spring Security has undergone some considerable changes and it has the potential to affect your journey migrating to Spring Boot 2.7 and eventually 3.x.

Spring Security 6.0, a major version bump, was released to be compatible with Spring Boot 3.1.x. To aid in this transition, the Spring Security maintainers released an interim 5.8.x release, and it needs to be performed against the latest Spring Boot 2.7.x release. Let's make these updates now.

**NOTE:** At the time of this writing, the current Spring Boot 2.7.x version is `2.7.14` and the current Spring Security 5.8.x version is `5.8.5`.

## Review our Upgrade Notes

Before we begin, remember that we're keeping detailed notes of the baseline state of our application as we upgrade it. Take a look at `upgrade-notes.md` to review where we are now.

```editor:open-file
file: ~/exercises/upgrade-notes.md
```
