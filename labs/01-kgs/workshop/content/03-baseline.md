Now that the code compiles, there are no skipped tests, and all tests pass we have a _Known Good State_. This is the ideal state to begin with for any upgrade or migration.

Let's document our baseline, so we can refer back to it and track out progress.

1. Create an upgrade notes file.

   Open the Editor and create a new file called `upgrade-notes.md` in the root of the repository.

   We're using a `.md` file because they render nicely in many editors.

2. Document the current Known Good State.

   Add a heading called `Initial Baseline`

   Document that the code compiles with no errors, not warnings, and all tests pass.

3. Commit all changes, including the new `upgrade-notes.md` file.

   Well, actually we won't be committing to the repository today in this online, hands-on lab environment.

   We will create this file on your behalf and updated it after each lab in this course. You'll be able to review it as needed.

   But, we recommend a process like the following in your own environment. We understand that you will have to do whatever is appropriate for your SDLC, but we're confident you get the idea.

   1. Create a branch called _"boot2.7-upgrade"_

      ```shell
      git switch -c "boot2.7-upgrade"
      ```

   2. Add new and modified files

      ```shell
      git add .
      ```

   3. Commit your changes to your _"upgrade"_ branch with a clear, unambiguous commit message.
