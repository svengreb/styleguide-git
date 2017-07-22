<p align="center"><img src="https://rawgit.com/arcticicestudio/styleguide-git/develop/src/assets/styleguide-git-banner-typography.svg"/></p>

<p align="center">The Arctic Ice Studio Git Style Guide.</p>

---

To present [Git commits](https://git-scm.com/docs/git-commit) in an organized, standardized, and easy-to-read manner, this official style guide describes how the content should be structured, organized, spelled and formatted in all Arctic Ice Studio projects.

There are only some strict rules but mostly guidelines since we are more interested in content than formatting and the review process may help contributors to conform to this guide later on.

## Introduction

Commit messages are important parts of communication between contributors and for the lifecycle of the project: its past and its future. It is the only place that captures not only what was changed, but why.

For open source project communities it is important to maintain good habits of communication in all forms. A well-crafted commit message can save a lot of time and overhead and helps to speed up development processes.

## Structural Split of Changes

> If a code change can be split into a sequence of patches/commits, then it should be split. *Less is not more.*

The cardinal rule for creating good commits is to **ensure there is only one logical change** per commit. There are many reasons why this is an important rule:

* **The smaller the amount of code** being changed, **the quicker and easier it is to review** and identify potential flaws.
* **Revert broken commits is much easier if there are not other unrelated code changes entangled with the original commit** if a change is found to be flawed later.
* **Small well defined changes will aid in isolating exactly where the code problem was introduced** when troubleshooting problems using Git's `bisect` capability.
* **Small well defined changes aid in isolating exactly where- and why a piece of code came from** when browsing history using Git `annotate` or `blame`.

### Bad Practices

* **Mixing whitespace changes with functional code changes**. The whitespace changes will obscure the important functional changes, making it harder for a reviewer to correctly determine whether the change is correct.
  * The change should be split into two commits, one with the whitespace changes, one with the functional changes.
* **Mixing two unrelated functional changes**. Without a structural split of changes it will be harder to identify flaws if two unrelated changes are mixed together. If it becomes necessary to later revert a broken commit, the two unrelated changes will need to be untangled, with further risk of bug creation.
* **Sending large new features in a single giant commit**. The code for a new feature is only useful when all of it is present, but this does not imply that the entire feature should be provided in a single commit.
  * New features may entail refactoring existing code so it is highly desirable that any refactoring is done in commits which are separate from those implementing the new feature. This helps reviewers and test suites validate that the refactoring has no unintentional functional changes.
  * Newly written code can often be split up into multiple pieces that can be independently reviewed. For example, changes which add new internal APIs/classes, can be in self-contained commits leading to easier code review and allows other developers to cherry-pick small parts of the work, if the entire new feature is not immediately ready for merge.
  * Code that affects public APIs should be done in commits separate from the actual internal implementation. This will encourage the author and reviewers to think about the generic API design, and not simply pick a design that is easier for their currently chosen internal implementation.

## Commit Messages

> The commit message must contain all the information required to fully understand & review the patch. *Less is not more*.

As important as the content of the change, is the content of the commit message describing it. The purpose of a commit message is to summarize a change, but the purpose of summarizing a change is to help to understand the code. The information to be put into a message should be valuable and useful for reviewers and the projects community.

Having a story in the Git history will make a huge difference in how others perceive the project. Taking great care in commit messages will help to increase the long-term overall quality.

* **The first line is important**. The [message summary](#message-summary) of the commit has special significance. It is used in many places like the Git history headline, git annotate- and merge messages or email subject lines where space is at a premium. As well as summarizing the change itself, it should take care to detail what part of the code is affected.
* **Describe the intent and motivation behind the changes**. Describe *why* the code has been written this way and document the overall code structure in the [message body](#message-body), particularly for large changes.
* **Include the GitHub issue ID and additional references** in the [message footer](#message-footer). This will automatically fire some hooks to track the commit in related GitHub repository issues- and pull requests and is **required to contribute to a project**.
* **Reviewers can understand what the original problem was**. The commit message should have a clear statement as to what the original problem is. The GitHub issue ID is merely interesting historical background on *how* the problem was identified and has been discussed within the community, but it should be possbile to review a proposed patch for correctness without having to read the whole ticket.

### Elements and their Structure

A Git commit message follows this format:
```
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

## Development

[![](https://img.shields.io/badge/Changelog-0.0.0-81A1C1.svg?style=flat-square)](https://github.com/arcticicestudio/styleguide-git/blob/v0.0.0/CHANGELOG.md) [![](https://img.shields.io/badge/Workflow-gitflow--branching--model-81A1C1.svg?style=flat-square)](http://nvie.com/posts/a-successful-git-branching-model) [![](https://img.shields.io/badge/Versioning-ArcVer_0.8.0-81A1C1.svg?style=flat-square)](https://github.com/arcticicestudio/arcver)

<p align="center"> <img src="http://arcticicestudio.com/favicon.ico" width=16 height=16/> Copyright &copy; 2017 Arctic Ice Studio</p>

<p align="center"><a href="http://www.apache.org/licenses/LICENSE-2.0"><img src="https://img.shields.io/badge/License-Apache_2.0-5E81AC.svg?style=flat-square"/></a>
