# Contributing

## Work against an Issue

For the vast majority of tasks, work should be done against a ticket (Issue).

If there isn't an issue for your piece of work already, create one. If there is, assign yourself.

This makes it much easier to track who is doing what, and what is to come.

### Creating issues

When creating an issue, clarify exactly what it is you want to add or solve, and if you have any, add initial implementation ideas. 

If you know of any, reference useful resources (blog posts, documentation, existing classes to be modified etc) in the issue.

Add labels to the issue, for example `documentation` for documentation issues, `idea` for stuff that needs further investigation, `deployment` for deployment/infrastructure related tickets etc. This allows people to filter issues when searching for work to do.

If appropriate, remember to add the issue to it's corresponding Milestone and Project.

## Clarify and Design First

When picking up issues, have a discussion to work out if the issue needs doing. Especially in older tickets, or those marked `idea`, for example, the issue may have gone stale, have already been done, or be redundant. If possible, have a discussion with whoever wrote the ticket first. Ensure you understand what needs doing.

Design first. Before writing any code, work out how the issue will be solved. Ideally put any implementation ideas/considerations in comments on the ticket (or write up a summary of any discussions) - this ensures that if someone else were to pick up the issue later, they'd know where to start.

## Testing

Use [Test Driven Development (TDD)](https://en.wikipedia.org/wiki/Test-driven_development) when writing code, whether that be fixing bugs, refactoring, or adding new features. This will help you solve any issues faster, and give confidence in the future, especially when refactoring.

Use unit tests to test individual bits of code (classes or public methods).

Use integration testing to test that components work together.

Use E2E testing to test the application works from a client point of view (for example automated UI testing, or testing responses from an exposed API).

Use load testing to test how the application will cope under heavier usage.

## PR (Pull Request) Guidelines

### Submitting PRs

Use a naming convention to explicitly categorize your PR, so a reviewer can gauge the effort required. Use:

`TRIVIAL/SP` for a tiny trivial change or spelling change.

`REFACTOR` for a pure refactor, where there are no functional changes.

`FAST_FOLLOW/FF` for changes coming from another PR review, see below for details.

`ISSUE/DEV/FEATURE` for larger changes that will likely require more carful review. 

Where appropriate, don't forget to reference the issue number. Use `Closes #issue_number` or `Fixes #issue_number` to close the ticket on merge. Use `See #issue_number` to reference the issue, without closing it

PRs should be kept as small as reasonably possible. This makes them easier to review and ensures they can be merged sooner rather than later. Don't be afraid to split a piece of work into multiple PRs!

If work needs to be done against an existing PR (i.e. if your work depends on a previous, open PR), create a second PR with the base branch set to your first PR. This means that when reviewing the second PR, only commits for that PR are shown. If the first PR is merged first, the base branch of the first PR will change to main automatically.

You should try and keep your individual commits clean, with useful messages. In reality though this doesn't always happen, PRs may end up with WIP or overly large commits. If this is the case, consider performing a squash merge when merging the PR, or squash the commits yourself before the PR is made.

Opportunistic refactoring is encouraged and should be separate PR.

### Reviewing PRs

Use a tagging convention for code review comments The submitter will then know which code review comments require what sort of action.

`BLOCKER` Must be fixed before merging
`FAST-FOLLOW/FF` Minor issue, can be fixed in subsequent PR, to help improve merge frequency.
`NIT` Doesn't need to be fixed. Trivial change, a comment, a question, etc.

Trivial changes don't need a detailed review! It’s OK to create pull requests that aren’t associated with a specific task as long as it's trivial. A trivial change, that passes all the automated checks, can be merged without review.

Refactors don't need a review if tested! If the code was covered and the refactored code remains covered no review is required.

**Larger changes are best checked out.** To review properly you need IDE support for navigation, you need to run the code, check the coverage, use the UI to test the interaction, etc. so check it out, your IDE may also support doing the review.

## Adding scripts

Scripts (usually Bash) should be added for repetitive tasks (for example, if files need downloading, setup commands need running). When adding bash scripts, use [Shellcheck](https://www.shellcheck.net/) for static analysis. 

If your script needs lots of environment variables to be set, or requires many arguments, consider using a `.env` file. Be careful not to add sensitive information (API keys for example) to source control. Consider using an example env file for people to copy from.

Add details of how/when to run any scripts in the project README, and ensure this is kept up to date if any scripts change.

## Formatting

For Java formatting, we use the [Google Style Guide](https://google.github.io/styleguide/javaguide.html). This is enforced by [Speedy Spotless](https://github.com/commitd/speedy-spotless) via [Maven](https://maven.apache.org/).

For Typescript formatting, we use [Prettier](https://prettier.io/).

Formatting should be run as a pre-commit hook, and a formatting error should fail the CI build.

## Dev Containers

[VSCode Dev Containers](https://code.visualstudio.com/docs/remote/containers) can be handy to use. They can ensure that everyone uses the same version of say, Maven or Yarn.

There is no obligation to use these of course, as everyone has their preference of editor, but they are worth considering, especially if working inside VSCode.

Dev Container configurations should be added to source control.
