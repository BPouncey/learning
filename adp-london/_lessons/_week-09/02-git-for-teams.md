---
layout: lesson
title: Git for Teams
lesson_date: 
---

## Pre-work

Prior to class, please review these sections from the Atlassian Git guide:

- [Merging vs. Rebasing](https://www.atlassian.com/git/tutorials/merging-vs-rebasing/conceptual-overview)
- [Branching](https://www.atlassian.com/git/tutorials/using-branches)
- [Comparing workflows](https://www.atlassian.com/git/tutorials/comparing-workflows)
- [Syncing](https://www.atlassian.com/git/tutorials/syncing)
- [A Successful Branching Model](http://nvie.com/posts/a-successful-git-branching-model/)
- [Semantic Versioning](http://semver.org/)
- [Git Hooks](https://git-scm.com/book/en/v2/Customizing-Git-Git-Hooks)

---

## Learning Objectives

- Implement the "Successful Branching Model".
- Understand Semver conventions.
- `merge` a "Release branch" into production.
- Create a feature branch and add a feature and use it to add a feature.
- `tag` a merge commit containing a production release using Semver conventions.
- `stash` some changes and re apply them to your code later.
- Use the `cherry-pick` command to add a commit from another branch without merging.
- Learn strategies for working with & maintaining repos with lot's of branches.
- Use a git hook to validate a `git commit`.

---

## Keywords

- Semver
- `merge`
- `tag`
- `stash`
- `cherry-pick`
- Git hooks
- Release
- Feature
- Feature branch
- Development branch

---

## Exercise 1

To warm up your git muscles, Please complete level 2 -> 4 on [learngitbranching.js.org](http://learngitbranching.js.org/)
When your finished, please spend 15 minutes capturing as much of what you discovered in your notes. THis will help us have a discussion later.

---

## Exercise 2

Git is a flexible tool. It has many options, but it does not force its users into any specific worlflows.
As a result, developers use git in a variety of ways.

Flexibility is is a double edge sword, as most developers who are new to git, will use  the set of commands they
are familiar with, and ignore other useful features.

- What are the features you are familiar with in Git. Discuss how you currently use git, with your nearest neighbour.

If you have not already, read ["A Successful Branching Model"](http://nvie.com/posts/a-successful-git-branching-model/).

- Why was this model developed?
- How is this model diffrernt from how you currently use git?
- How does this model help developers build software?
- Could you make this model better?

---

## Exercise 3

In your own words, explain to your neighbour why you would use the following git commands:

- Rebase
- Stash
- Merge
- Cherry-pick

---

## Lab Activity

In today's Lab we'll set up our GitHub environment for our Community Projects, which will begin next week. 

### Install the ZenHub Chrome extension.

The ZenHub extension turns github into a project menagement platform. We'll be using the 'Boards' feature. Boardsis a simple Kanban system for 
tracking issues as tasks in github.

**Set up the following Boards:**

- New issues
- In Progress
- Review / QA
- Closed

### Issue Lifecycle Demo

Once the board is set up, as a class we'll demonstrate an issue lifecycle from creation, to feature-branch to commit & merge into master.
We'll be using the git-flow techniques to manage commits into this repository. *All commmits to master must be in the form of a pull request* 


---

## Additional Resources

- [Git for Teams](http://gitforteams.com/) (O'Reilly book resources)
- [Git for Teams](https://gitlab.com/gitforteams/gitforteams) (Gitlab resource)