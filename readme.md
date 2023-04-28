<p align="center">
  <picture>
    <source srcset="https://raw.githubusercontent.com/svengreb/assets/main/static/images/logos/projects/styleguides/git/heroes/dark.svg?sanitize=true" width="100%" media="(prefers-color-scheme: light), (prefers-color-scheme: no-preference)" />
    <source srcset="https://raw.githubusercontent.com/svengreb/assets/main/static/images/logos/projects/styleguides/git/heroes/light.svg?sanitize=true" width="100%" media="(prefers-color-scheme: dark)" />
    <img src="https://raw.githubusercontent.com/svengreb/assets/main/static/images/logos/projects/styleguides/git/heroes/dark.svg?sanitize=true" width="100%" />
  </picture>
</p>

<p align="center">
  <a href="https://github.com/svengreb/styleguide-git/releases/latest" target="_blank">
    <img src="https://img.shields.io/github/release/svengreb/styleguide-git.svg?style=flat-square&label=Release&logo=github&logoColor=eceff4&colorA=4c566a&colorB=88c0d0" />
  </a>
  <a href="https://github.com/svengreb/styleguide-git/blob/main/changelog.md" target="_blank">
    <img src="https://img.shields.io/github/release/svengreb/styleguide-git.svg?style=flat-square&label=Changelog&logo=github&logoColor=eceff4&colorA=4c566a&colorB=88c0d0" />
  </a>
</p>

<p align="center">
  <a href="https://github.com/svengreb/styleguide-markdown/releases/latest" target="_blank">
    <img src="https://img.shields.io/github/release/svengreb/styleguide-markdown.svg?style=flat-square&label=Markdown%20Style%20Guide&colorA=4c566a&colorB=88c0d0&logo=data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIzOSIgaGVpZ2h0PSIzOSIgdmlld0JveD0iMCAwIDM5IDM5Ij48cGF0aCBmaWxsPSJub25lIiBzdHJva2U9IiNEOERFRTkiIHN0cm9rZS13aWR0aD0iMyIgc3Ryb2tlLW1pdGVybGltaXQ9IjEwIiBkPSJNMS41IDEuNWgzNnYzNmgtMzZ6Ii8%2BPHBhdGggZmlsbD0iI0Q4REVFOSIgZD0iTTIwLjY4MyAyNS42NTVsNS44NzItMTMuNDhoLjU2Nmw1Ljg3MyAxMy40OGgtMS45OTZsLTQuMTU5LTEwLjA1Ni00LjE2MSAxMC4wNTZoLTEuOTk1em0tMi42OTYgMGwtMTMuNDgtNS44NzJ2LS41NjZsMTMuNDgtNS44NzJ2MS45OTVMNy45MzEgMTkuNWwxMC4wNTYgNC4xNnoiLz48L3N2Zz4%3D"/>
  </a>
  <a href="https://github.com/svengreb/styleguide-javascript/releases/latest" target="_blank">
    <img src="https://img.shields.io/github/release/svengreb/styleguide-javascript.svg?style=flat-square&label=JavaScript%20Style%20Guide&logoColor=eceff4&colorA=4c566a&colorB=88c0d0&logo=javascript" />
  </a>
  <a href="https://github.com/svengreb/styleguide-git/releases/latest" target="_blank">
    <img src="https://img.shields.io/github/release/svengreb/styleguide-git.svg?style=flat-square&label=Git%20Style%20Guide&logoColor=eceff4&colorA=4c566a&colorB=88c0d0&logo=git" />
  </a>
</p>

<p align="center">An opinionated, yet universally applicable <a href="https://git-scm.com" target="_blank">Git</a> style guide.</p>

To present Git [commits][2] and [branches][1] in an organized, standardized, and easy-to-read manner, this style guide describes how the content should be structured, spelled and formatted.

There are only some strict rules but mostly guidelines since we are more interested in content than formatting while the review process might help contributors to conform to this guide later on.

## Introduction

Commit messages are important parts of communication between contributors and the lifecycle of a project: its past and its future. It is the only place that captures not only what was changed, but why.

For open source project communities it‘s important to maintain good habits of communication in all forms. A well-crafted commit message can save a lot of time, overhead and helps to speed up development processes.

## Structural Split Of Changes

> If a code change can be split into a sequence of patches/commits, then it should be split.
> _Less is not more_.

The cardinal rule for creating good commits is to **ensure there is only one logical change** per commit. There are many reasons why this is an important rule:

- **The smaller the amount of code** being changed, **the quicker and easier it is to review** and identify potential flaws.
- **Revert broken commits is much easier if there are not other unrelated code changes entangled with the original commit** if a change is found to be flawed later.
- **Small well defined changes will aid in isolating exactly where the code problem was introduced** when troubleshooting problems using Git‘s `bisect` capability.
- **Small well defined changes aid in isolating exactly where- and why a piece of code came from** when browsing history using Git `annotate` or `blame`.

### Bad Practices

- **Mixing whitespace changes with functional code changes**. The whitespace changes will obscure the important functional changes, making it harder for a reviewer to correctly determine whether the change is correct.
  - The change should be split into two commits, one with the whitespace changes, one with the functional changes.
- **Mixing two unrelated functional changes**. Without a structural split of changes it will be harder to identify flaws if two unrelated changes are mixed together. If it becomes necessary to later revert a broken commit, the two unrelated changes will need to be untangled, with further risk of bug creation.
- **Sending large new features in a single giant commit**. The code for a new feature is only useful when all of it is present, but this does not imply that the entire feature should be provided in a single commit.
  - New features may entail refactoring existing code so it is highly desirable that any refactoring is done in commits which are separate from those implementing the new feature. This helps reviewers and test suites validate that the refactoring has no unintentional functional changes.
  - Newly written code can often be split up into multiple pieces that can be independently reviewed. For example, changes which add new internal APIs/classes, can be in self-contained commits leading to easier code review and allows other developers to cherry-pick small parts of the work, if the entire new feature is not immediately ready for merge.
  - Code that affects public APIs should be done in commits separate from the actual internal implementation. This will encourage the author and reviewers to think about the generic API design, and not simply pick a design that is easier for their currently chosen internal implementation.

## Commit Messages

> The commit message must contain all the information required to fully understand & review the patch.
> _Less is not more_.

As important as the content of the change is the content of the commit message describing it. The purpose of a commit message is to summarize a change, but the purpose of summarizing a change is to help to understand the code. The information to be put into a message should be valuable and useful for reviewers and the projects community.

Having a story in the Git history will make a huge difference in how others perceive the project. Taking great care in commit messages will help to increase the long-term overall quality.

- **The first line is important**. The [message summary](#message-summary) of the commit has special significance. It is used in many places like the Git history headline, git annotate- and merge messages or email subject lines where space is at a premium. As well as summarizing the change itself, it should take care to detail what part of the code is affected.
- **Describe the intent and motivation behind the changes**. Describe _why_ the code has been written this way and document the overall code structure in the [message body](#message-body), particularly for large changes.
- **Include the GitHub issue ID and additional references** in the [message footer](#message-footer). This will automatically fire some hooks to track the commit in related GitHub repository issues- and pull requests and is **required to contribute to a project**.
- **Reviewers can understand what the original problem was**. The commit message should have a clear statement as to what the original problem is. The GitHub issue ID is merely interesting historical background on _how_ the problem was identified and has been discussed within the community, but it should be possbile to review a proposed patch for correctness without having to read the whole ticket.

### Elements and their structure

A Git commit message follows this format:

```raw
<summary>

<body>

<footer>
```

#### Message Summary

The first line is the one-sentence concise subject about the changes introduced by the commit. The **optimal total size of characters is 50 or less**, but is **limited to 72 characters** and **does not ended with a period**. It uses the **imperative mood** and is **separated from the [message body](#message-body) by a single blank line**.

Technical details that cannot be expressed in these strict size constraints should be put in the message body instead.

#### Message Body

The detailed description about the changes of the commit should be split into **multiple logically separate paragraphs** if necessary. It uses the **imperative mood** and the lines are **wrapped at 72 characters**.

#### Message Footer

This metadata block **must contain the GitHub issue ID** and is **separated from the [message body](#message-body) by a single blank line**.

**Multiple issues are separated by a comma** and **additional references** can be added in the next lines.

## Branch Naming

> A branch should reflect the story of the commits it contains using a valuable and useful name to clarify its purpose during the development lifecycle and the persistency in the history.

This style guide follows the [GitHub Flow][3] branching model with the deviations and additional conventions described below.

Branches are an important major component for building open source projects regardless of the size. A well maintained branch merge story in the history will help to increase the long-term overall quality.

### Core Branches

The infinite lifecycle core branch must be lowercase named `master`.

### Story Branches

The lowercase name of a limited development lifecycle story branch must reflect the _type_ separated by a slash from the _issue ID_ and followed by the short and descriptive _title_ using hyphen delimiters.

```raw
<TYPE>/<ISSUE_ID>-<TITLE>
```

Example: `feature/gh-17-tokenizer-api`

#### Story Type Prefixes

- `bugfix`
- `feature`
- `improvement`
- `release`
- `subtask`
- `task`
- `test`

Every branch must contain _issue ID_ which is important to automatically fire some hooks to track the commit in the related GitHub repository issues and pull requests and is **required to contribute to a project**.

A `release` branch is used to prepare a new [tagged](#tags) release version.

## Tags

This style guide follows the [GitHub Flow][3] branching model with the deviations and additional conventions described below using the [“Semantic Versioning 2“ specification][4].

All version tags are created in the `master` [core branch](#core-branches) to specify which commits reflects a release version as defined by the `release` [branch name](#branch-naming) prefix.

- **Only use annotated tags**. Allows to include the name of the project followed by the version number to the commit message.
- **Always add the `v` prefix character to version tags**. Clarifies the tag type as specified by [SemVer][4].
- **Every version tag must be signed**. Ensures that the version has been tested and approved by the project owner or an authorized project contributor.

<p align="center">
  <picture>
    <source srcset="https://raw.githubusercontent.com/svengreb/assets/main/static/images/elements/separators/logo/footer/dark/spaced.svg?sanitize=true" width="100%" media="(prefers-color-scheme: light), (prefers-color-scheme: no-preference)" />
    <source srcset="https://raw.githubusercontent.com/svengreb/assets/main/static/images/elements/separators/logo/footer/light/spaced.svg?sanitize=true" width="100%" media="(prefers-color-scheme: dark)" />
    <img src="https://raw.githubusercontent.com/svengreb/assets/main/static/images/elements/separators/logo/footer/dark/spaced.svg?sanitize=true" width="100%" />
  </picture>
</p>

<p align="center">
  Copyright &copy; 2016-present <a href="https://www.svengreb.de" target="_blank">Sven Greb</a>
</p>

<p align="center">
  <a href="https://github.com/svengreb/styleguide-git/blob/main/license" target="_blank">
    <img src="https://img.shields.io/static/v1.svg?style=flat-square&label=License&message=MIT&logoColor=eceff4&colorA=4c566a&colorB=88c0d0" />
  </a>
  <a href="https://www.svengreb.de">
    <img src="https://img.shields.io/static/v1.svg?style=flat-square&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABAAAAAQCAYAAAAf8/9hAAAABmJLR0QA/wD/AP+gvaeTAAABMklEQVQ4jcWQvUoDQRRGz52s5IfVIiDWPkGKFFaCIVaGdIagjcFAwICFb7DvIK6QQlNpY2UQLMQVBbEQ0SewFkGbKCQmOzaTJay7/lR+zTAf9xwuF/47Mv45rdezqWEq72v/RWZnHgqOMwDwHMfSj085JSqb6Pu38we7r18E3nqzhmYbsE11rxKsAvhDfQiSM30XYbOw57YDwfnaRl6U3ABWaMNn806H+oGPzBX3d+4UgChZiYBHYBgGsBLoKoAyhR0x9G20Zmpc4P1ZoMQDcwMNclFrdhBKv6M5WWi7ZQGtjEUn35IV4OwnVjSX/WGmKqCDDUa5rmyle3bvGFiMg3WGUsF1u0EXHoqTRMGRgkAy2eugKZrqijRLYThWANBpNDL2h3UE0J0YLJdbrfe42f/NJ0wqY7/KcXKPAAAAAElFTkSuQmCC&label=lovely%20crafted%20in&message=Germany&colorA=4c566a&colorB=88c0d0" />
  </a>
</p>

[1]: https://git-scm.com/docs/git-branch
[2]: https://git-scm.com/docs/git-commit
[3]: https://docs.github.com/en/get-started/quickstart/github-flow
[4]: https://semver.org/spec/v2.0.0.html
