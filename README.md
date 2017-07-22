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

## Development

[![](https://img.shields.io/badge/Changelog-0.0.0-81A1C1.svg?style=flat-square)](https://github.com/arcticicestudio/styleguide-git/blob/v0.0.0/CHANGELOG.md) [![](https://img.shields.io/badge/Workflow-gitflow--branching--model-81A1C1.svg?style=flat-square)](http://nvie.com/posts/a-successful-git-branching-model) [![](https://img.shields.io/badge/Versioning-ArcVer_0.8.0-81A1C1.svg?style=flat-square)](https://github.com/arcticicestudio/arcver)

<p align="center"> <img src="http://arcticicestudio.com/favicon.ico" width=16 height=16/> Copyright &copy; 2017 Arctic Ice Studio</p>

<p align="center"><a href="http://www.apache.org/licenses/LICENSE-2.0"><img src="https://img.shields.io/badge/License-Apache_2.0-5E81AC.svg?style=flat-square"/></a>
