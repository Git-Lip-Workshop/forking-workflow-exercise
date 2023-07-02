

## Exercise: practice collaborative forking workflow

In this exercise, we make a fork, push to that fork, and make a pull
request to the "central" repository. Later we will exercise updating the individual forks
after changes from all participants have been merged.

As an example we will collaboratively develop a cookbook for taco recipes,
inspired by [tacofancy](https://github.com/sinker/tacofancy).

Objectives:

- Learn how to to contribute to an open-source project, following the forking workflow.
- Learn how to update your fork with upstream changes.


### Part A: Fork and clone

First fork this repository into your namespace and then clone the fork to your computer.

```shell
git clone https://github.com/<username>/forking-workflow-exercise.git
```

### Part B: Select an existing or open a new "Issue" to tacke

Before we start any coding, navigate to the list of open issues on the central
repository. Select one issue to tacke or create a new issue, where you describe
a new idea for a recipe. After selecting or creating an issue, note it's number.
We will later refer to this issue number.

### Part C: Create a branch, make a change and commit
Before we do any modification, we create a new branch and switch to it: this is
a good reflex and a good practice. Choose a branch name which is descriptive of
its content. 

```shell
git switch -c <branch name>
git push --set-upstream origin <branch name>
```

On the new branch create a new file which will hold your recipe,
for instance `my_recipe.md` (but change the name). You can get inspired
[here](https://github.com/sinker/tacofancy/tree/master/full_tacos). Hopefully we all use different
file names, otherwise we will experience conflicts later (which is also interesting!).

There is also a file called `test.py` which will automatically verify whether your recipe contains the string
"taco" (case insensitive). This is there to slowly introduce us to automated testing.

Once you are happy with your recipe, commit the change and in your commit
message reference the issue which you have opened earlier with "<commit msg> ; closes #N". 
Use a desciptive message and replace N by the actual issue number.

```shell
git add my_recipe.md
git commit -m "<commit-msg; closes #N"
```

### Part D: Push your changes to the fork

Now push your new branch to your fork. Your branch is probably called something else than "feature". Also verify where
"origin" points to.

```shell
$ git push origin <branch name>
```


### Part E: File a pull request

Then open a pull request from the branch on your fork towards the master branch on the repository where you forked from.

Observe how the issues automatically close after the pull requests are merged
(provided the commit messages contain [the right keywords](https://help.github.com/en/articles/closing-issues-using-keywords)).


### Part F: Update your fork

As other changes are integrated in the original repository, it's good practice
to keep your forked repo up-to-date with the upstream repository.

To do this, add the original repository as a remote in your local copy of
the forked repository and pull the changes from the remote.

```shell
git remote add upstream https://github.com/leonor-loureiro/forking-workflow-exercise.git
git merge upstream
```

