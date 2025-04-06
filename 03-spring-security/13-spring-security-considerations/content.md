This module focuses on Spring Security. Your application is compiling, but if you're using Spring Security, now's a good time to review your code and configuration, to ensure you're doing things based on the most current version. This will pay dividends later when you upgrade to Spring Boot 2.7 and eventually 3.x.

We're going to recommend that you familiarize yourself with the new features and bug fixes associated with Spring Security, that come with the upgrade to Spring Boot 2.7. However, we also want you to understand that as a matter of practice, the Spring Security team does not make breaking changes or deprecations over minor versions. That means any work you perform related to Spring Security is elective and preparatory to a major version upgrade, such as upgrading to Spring Boot 3.

## Spring Security Specific Upgrade

Let's run a mini "Upgrade" path, just for Spring Security.

### Prep

1. Review the Spring Security release notes for Spring Security 5.5 to 5.7

   - [Spring Security 5.5](https://github.com/spring-projects/spring-security/releases/tag/5.5.0)
   - [Spring Security 5.6](https://github.com/spring-projects/spring-security/releases/tag/5.6.0)
   - [Spring Security 5.7](https://github.com/spring-projects/spring-security/releases/tag/5.7.0)

2. Re-review the Spring Boot 2.6 and 2.7 Release Notes. Look for any mentions/impacts related to Spring Security.

   - [2.6 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.6-Release-Notes)
   - [2.7 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.7-Release-Notes)

3. Review any Spring team blog posts related to the upgrades that might contain information or details related to the upgrade. These often provide insights into hurdles you could face, or recommendations of things to do to prepare for the next release upgrade.

   - [Upgrading Spring Boot 2.5 to 2.6](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.6-Release-Notes#upgrading-from-spring-boot-25)
   - [Upgrading Spring Boot 2.6 to 2.7](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.7-Release-Notes#upgrading-from-spring-boot-26)

4. Review the Spring Boot 3 and Spring Security Preparing For 6 Guides. This will provide you an opportunity to decide whether you want to make some or all of the recommended changes now, to facilitate the Spring Boot 3 upgrade later.

   - [Spring 3.0 Migration Guide](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-3.0-Migration-Guide)
   - [Spring Security Preparing for 6.0 Guide](https://docs.spring.io/spring-security/reference/5.8/migration/index.html)

@@@alert
{
"text": "Out of all the documents above, the most important and actionable items at this time are contained in the [Spring Security Preparing for 6.0 Guide](https://docs.spring.io/spring-security/reference/5.8/migration/index.html). This highlights things you should consider doing now, so that your transition to Spring Boot 3 and Sprint Security 6 will be much easier.",
"type": "info"
}
@@@

### Assess

Review your application source and configuration. Is your application impacted? Are there things you saw in the Preparing for 6 guide that you'll want to act upon?

### Update

If you've decided to make changes to your application, make them one at a time, compiling in-between. Remember **SCAR**!

@@@alert
{
"text": "We came into this module with application source code that was compiling successfully and it is important that we leave this module the same way!",
"type": "warning"
}
@@@

### Test and Release

We'll perform these steps as part of the overall upgrade process.

## Establish a New Baseline

Document the current state in writing and in source control.

1. Take note of any errors, warnings, or issues in the "Upgrade-Notes.md"
   1. Append a new heading to the document titled - "Upgrade Spring Security Version".
   2. Document any remaining warnings, or other known issues.
2. Issue a commit.
