Now that our dependencies are under control, we'll want to address any error and/or warning messages during compilation.

In this lesson, we'll resolve any remaining findings using the **SCAR** method, and focus on achieving successful compilation of our application source.

## Errors and Warnings

Every time we compile the build tool, compiler provides us with information about the state of the source code. It'll indicate any of the following things, wherever applicable:

- Errors
- Warnings
- Deprecations

Let's address each of these, in turn.

## Errors: Fixing the Build

If we're seeing errors, we won't be able to successfully compile the application. So, these should be addressed first.

Regardless of whether we're working to resolve an error, a warning, or a Deprecation, the process is going to be the same. We'll use the **SCAR** method, modify the build definition, and/or source, as required to resolve the issue.

**Tip:** If you need more detailed information, modify the maven command line with one of the following: `-x`, `--debug`, or `-e`. For example:

```shell
$ ./mvnw compile -x
```

### Steps to Fixing the Build

Follow these steps to get the code to compile.

1. Review the build tool/compiler output. What's it telling us? Be sure to review the entire output!

   If you see multiple related errors, address these first. One solution could solve them all.

   Things to look for:

   - Do we have a version compatibility problem?

     Remember, you can use the `dependency:tree` task to find out if two dependencies want different versions of the same common dependency.

     ```shell
     $ mvnw dependency:tree
     ```

   - Does our source code need to change?
     Maybe something was deprecated in a dependency and we need to change our source based on the new way.

   - Has something changed in the namespacing of a dependency? Example: `javax.servlet` vs `jakarta.servlet`

2. React - Make a small change and compile the code again
3. Is the issue resolved?
   - **Yes** - Move on to the next issue.
   - **No** - Make another small change and React again.
4. Repeat the process until all issues are resolved.

## Warnings TODAY, Errors TOMORROW!

While you may believe that warning messages are no big deal, it's a best practice to mitigate them.

Leaving a compile with warnings can be confusing for other developers who don't have the full context that you do.

Ultimately, the decision is for you and your team to make regarding how much time and effort you spend resolving warnings.

Just remember, a warning _TODAY_ might become an error, CVE, or defect _TOMORROW_. Make good choices!

If all errors and/or warnings have been resolved (to your satisfaction), then congratulations! You now have a working compile using the updated Spring Boot version.

But, what about Deprecations?

## Deprecations

We should also be cognizant of Deprecations. We discussed this during the _Preparing to upgrade_ lesson of this course. Now would be a good time to revisit the subject in a little more detail.

Spring Framework and Spring Boot are continually evolving. With evolution, change will come. For every release of the frameworks, Deprecations are always highlighted at the end of the version migration guides. Deprecations are maintained for one minor release.

We should take note of the Deprecations in each release we're upgrading to, and see if they affect our current codebase. For the purposes of this course, the Deprecations that must be handled are related to Spring Boot 2.4 and 2.5. It is recommended that Deprecations within **2.6 and 2.7** also be resolved. Strictly speaking, though, this isn't required.

- [2.4 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.4-Release-Notes)
- [2.5 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.5-Release-Notes)
- [2.6 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.6-Release-Notes)
- [2.7 Release Notes](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.7-Release-Notes)

For example, the **2.7 Release Notes** [list these Deprecations](https://github.com/spring-projects/spring-boot/wiki/Spring-Boot-2.7-Release-Notes#deprecations-in-spring-boot-27). Do they impact your application? You'd better find out!

Once you've addressed all errors, warnings, and deprecations to your satisfaction, it's time to baseline again!

## Establish a New Baseline

Document the current state in writing and in source control.

1. Take note of any errors, warnings, or issues in the "Upgrade-Notes.md"
   1. Append a new heading to the document titled - "Successful Compile".
   2. Document any remaining warnings or other known issues.
2. Issue a commit.
