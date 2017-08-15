# Git workflow for small teams

Git is version control system for tracking changes in the files that is useful for collaborative code development. In particular, it allows to keep the code base reusable and maintainable. Git can be used in single user mode, but it is also used by extremely large projects such as the Linux Kernel or Windows 10 at Microsoft. Due to it's extensive functionality it can be somewhat confusing for new user, and while a number of git tutorials exists online, picking the right one for your use case is not necessary straightforward. In practice, most git users use a fairly small subsets of git commands that is sufficient for their use case.  

In this tutorial we will outline a simple workflow for using git in combination with Github suitable for small teams. This workflow is adapted from the one used in the open source Python community and is therefore suitable for both open-source and commercial projects (in private repositories). 



**Prerequisites**: you have installed git and setup an online Github repository. You know how to commit and push new changes to this repository. For instance, see [try.github.io](https://try.github.io) for an introductory git tutorial.

**Note:**  in this tutorial we will illustrate the use of this workflow with Github, but it can easily be used with any other online git hosting service such as Bitbucket, GitLabs etc.

## Repository setup

Here we assume that a team is working collaboratively on a git repository stored online. All team members have write access to the repository and are able to create new branches (if that is not the case the example of use of Github "forks" below for a more general setup). The `master` branch contains the stable version of the code. We can clone the repository locally with,

```
git clone <repository-url>
```
and run,
```
cd <repository-path>
```
to make sure we are inside the repository folder. This tutorial focuses on the command line usage as the preferred way of interacting with Git. We will illustrate the


## Adding changes to the repository

In the proposed workflow making any changes to the repository, can be summarized to the following steps,
  1. Switching to the master branch
  2. Synchronizing with the upstream repository
  3. Creating a new branch, adding code changes, and pushing the changes
     
 <img src="../_static/git_workflow_1.png" alt="Basic git worflow" style="width: 50%;     display: block; margin: 0 auto;"/>

  4. Making a pull request online
  5. Reviewing and merging the pull request


It is important to execute each of the above steps and understand what they are doing. Frequent issues new git users get usually result from missing one of the first few steps.   


## Git workflow details

#### 1. Switching to the master branch


**Note:** the same approach could be used to checkout any other branch as well.

First let's check the branch we are currently on with,

```
git branch
```
it the above command doesn't return `master`, we can switch to `master` with,
```
git checkout master
```
#### 2. Synchronizing with the upstream repository

To synchronize the current branch with an upstream repository, run,

```
git fetch
git rebase origin/master
```
**Note:** the above command could be replaced with `git pull`, however the latter while can also add [undesirable side effects](https://stackoverflow.com/a/15316602/1791279).

**Note 2:** The rebase can occasionally result in a merge conflict, that need to be resolved (see ["Resolving merge conflicts after a Git rebase"](https://help.github.com/articles/resolving-merge-conflicts-after-a-git-rebase/))

#### 3. Creating a new branch, adding code changes, and pushing the changes

We can now create a new branch `new-feature` with,
```
git checkout -b new-feature
```

It is recommender to use a branch name suggestive of the planned modifications.

One this new branch we can, stage new files for a commit with,

```
git add <list-of-changed-files>
```
that can then be commited with,
```
git commit -a
```
Finally, we push the commit to the upstream repository with,
```
git push
```

#### 4. Creating a pull request

Once the branch with our modification is pushed to Github, we need to create a Pull Request (PR) i.e. a request to merge our changes with the `master` branch. This process is discussed in detail in the [Github Documentation](https://help.github.com/articles/creating-a-pull-request/#creating-the-pull-request)

#### 5. Reviewing and merging the Pull Request (PR)

Once the PR is submitted on Github, we should,

 * wait for the Continuous Integration services to run the test suite (if any are setup, see last section of the tutorial).
 * [code review](https://help.github.com/articles/about-pull-request-reviews/) the PR by other team members
 * merge the PR to the master branch using the "Merge Pull Request" button.

Users can then synchronise their local repository as discussed in section 2.


## Further reading
 
 * Setting up [continious integration](http://python-guide-ru.readthedocs.io/en/latest/scenarios/ci.html)
 * [Using Github forks](https://help.github.com/articles/fork-a-repo/)
