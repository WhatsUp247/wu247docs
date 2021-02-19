# Contributing

Your first step is to establish a public repository from which we can pull your work into the master repository. We recommend using [GitHub](https://github.com), as that is where the component is already hosted.

1. Setup a [GitHub account](http://github.com/), if you haven't yet
2. Clone the desired repository locally and enter it.

```zsh
% git clone https://github.com/WhatsUp247/{repo_name}.git
% cd {repo_name}
```

## Keeping Up-to-Date

Periodically, you should update your master branch to have the latest code that is on the live site:

```zsh
% git checkout master
% git pull origin master
```

If you're tracking other branches -- for example, the "develop" branch, where new feature development occurs -- you'll want to do use:

```zsh
% git checkout develop
$ git fetch origin
$ git rebase master
$ git push origin develop
```

## Working on a patch

We recommend you do each new feature or bugfix in a new branch. This simplifies the task of code review as well as the task of merging your changes into the
main branch.

A typical workflow will then consist of the following:

1. Create a new local branch based off either your master or develop branch.
2. Switch to your new local branch. (This step can be combined with the previous step with the use of `git checkout -b`.)
3. Do some work, commit, repeat as necessary.
4. Push the local branch to your remote repository.
5. Submit a pull request.

The mechanics of this process are actually quite trivial. Below, we will create a branch for fixing an issue in the tracker.

```zsh
% git checkout -b fix-ws219
```

Switched to a new branch 'fix-ws219'
... do some work ...

```zsh
% git commit
```

... write your log message ...

```zsh
% git push origin fix-ws219
```

To submit a pull request:

1. **Navigate** to your repository
2. **Select** the branch you just created
3. **Select** the "Pull Request" button in the upper right
4. **Select** the Dominic Cartwright as the reviewer
5. **Assign** your self to the pull request

### What branch to issue the pull request against?

Which branch should you issue a pull request against?

-   For fixes against the stable release, issue the pull request against the "master" branch.
-   For new features, or fixes that introduce new elements to the public API (such as new public methods or properties), issue the pull request against the "develop" branch.

## Development Branching Process

-   **Start of new work**:

    ```zsh
    % git checkout master
    % git fetch origin master
    % git checkout -b {feature_branch_name}
    ```

    Work on the project or bug.

-   **Completed work**:

    ```zsh
    % git commit
    % git push origin {feature_branch_name}
    ```

    Submit a pull request. Select Dominic Cartwright as a reviewer and assign yourself to the pull request.
    If the pull request states that there are merge conflicts, resolve them.

-   **Finished work not ready for merging with master**:

    ```zsh
    % git checkout -b  {feature_branch_name}
    % git commit
    % git push origin {feature_branch_name}
    ```

## Local Branch Reset from Remote Branch

```zsh
% git reset --hard {commit id}
```

OR

```zsh
% git reset --hard origin/{branch}
```

## Branch Cleanup

As you might imagine, if you are a frequent contributor, you'll start to get a ton of branches both locally and on your remote. Once you know that your changes have been accepted to the master repository, we suggest doing some cleanup of these branches. When you merge a pull request in Github, there is a option to delete the branch associated with the pull request. This is good practice to do especially after bug fixes. However, we can use the following commands to clean up branch that have been left over for various reasons.

-   Local branch cleanup

    ```zsh
    % git branch -d {branchname}
    ```

-   Remote branch removal

    ```zsh
    % git push {username} :{branchname}
    ```

    OR

    ```zsh
    % git push origin --delete {branchname}
    ```
