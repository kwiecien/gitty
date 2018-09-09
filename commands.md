# git log

```bash
git log --oneline
git log --stat
```
```bash
git log --oneline --graph --decorate
```

All branches:

    git log --oneline --graph --decorate --all

Show changes introduced in the parent commit:

    git log --patch
    git log -p
    git show

## [Filtering the Commit History](https://www.atlassian.com/git/tutorials/git-log)

-   By Amount
    ```bash
    git log -3
    ```
-   By Date

    To display all the commits added between July 1st, 2014 and July 4th, 2014, you would use the following:

    ```bash
    git log --after="2014-7-1" --before="2014-7-4"
    ```

-   By Author

    The following command searches for commits by either Mary or John

    ```bash
    git log --author="John\|Mary"
    ```

-   By Message

    For example, if your team includes relevant issue numbers in each commit message, you can use something like the following to pull out all of the commits related to that issue (you can also pass in the -i parameter to git log to make it ignore case differences while pattern matching):

    ```bash
    git log -i --grep="JRA-224:"
    ```

-   By File

    For example, the following returns all commits that affected either the foo.py or the bar.py file (the -- parameter is used to tell git log that subsequent arguments are file paths and not branch names):

    ```bash
    git log -- foo.py bar.py
    ```

-   By Content

    If you want to know when the string Hello, World! was added to any file in the project, you would use the following command:

    ```bash
    git log -S"Hello, World!"
    git log -G"<regex>"
    ```

-   By Range

     You can pass a range of commits to git log to show only the commits contained in that range.

    ```bash
    git log <since>..<until>
    git log master..feature
    ```

-   Merges
    ```bash
    git log --no-merges
    git log --merges
    ```

# git tag

    git tag -a v1.0

The -a flag is used. This flag tells Git to create an annotated flag. If you don't provide the flag (i.e. git tag v1.0) then it'll create what's called a lightweight tag.

Annotated tags are recommended because they include a lot of extra information such as:

-   the person who made the tag
-   the date the tag was made
-   a message for the tag

Because of this, you should always use annotated tags.

It will display all tags that are in the repository:

    git tag

A Git tag can be deleted:

    git tag -d v1.0

Running git `tag -a v1.0` will tag the most recent commit. If you wanted to tag a commit that occurred farther back in the repo's history, you have to do is provide the SHA of the commit you want to tag:

    git tag -a v1.0 SHA

# git branch

Adding a branch to the specific commit:

    git branch feature sha1sha

Create a new branch and have this branch start at the same location as the master branch:

    git checkout -b feature master

# git revert

The command undo the changes that were made by the provided commit. It also provides a commit message of the commit that was reverted. Furthermore, it creates a new commit to record this change.

    git revert shaOfCommitToRevert

# Relative commits

The main difference between the `^` and the `~` is when a commit is created from a merge. A merge commit has two parents. With a merge commit, the `^` reference is used to indicate the first parent of the commit while `^2` indicates the second parent. The first parent is the branch you were on when you ran `git merge` while the second parent is the branch that was merged in.

```bash
* 9ec05ca (HEAD -> master) Revert "Set page heading to "Quests & Crusades""
* db7e87a Set page heading to "Quests & Crusades"
*   796ddb0 Merge branch 'heading-update'
|\
| * 4c9749e (heading-update) Set page heading to "Crusade"
* | 0c5975a Set page heading to "Quest"
|/
*   1a56a81 Merge branch 'sidebar'
```

-   `^` indicates the **parent** commit
-   `~` indicates the **first parent** commit

Let's look at how we'd refer to some of the previous commits. Since HEAD points to the 9ec05ca commit:

-   HEAD^ is the db7e87a commit
-   HEAD~1 is also the db7e87a commit
-   HEAD^^ is the 796ddb0 commit
-   HEAD~2 is also the 796ddb0 commit
-   HEAD^^^ is the 0c5975a commit
-   HEAD~3 is also the 0c5975a commit
-   HEAD^^^2 is the 4c9749e commit (this is the grandparent's (HEAD^^) second parent (^2))

# git reset

Reverting creates a new commit that reverts or undos a previous commit. Resetting, on the other hand, **erases** commits!

    git reset <reference-to-commit>

`git reset` can be used to:

-   move the HEAD and current branch pointer to the referenced commit
-   erase commits
-   move committed changes to the staging index
-   unstage committed changes

##### Git Reset's Flags

The way that Git determines if it erases, stages previously committed changes, or unstages previously committed changes is by the flag that's used. The flags are:

-   `--mixed` running `git reset --mixed HEAD^` will take the changes made in the last commit and move them to the **working directory**
-   \--soft  running `git reset --soft HEAD^` will take the changes made in the last commit and move them to the **Staging Index**
-   \--hard running `git reset --hard HEAD^` will take the changes made in the last commit and **erases** them

# git diff

-   By default git diff will show you any uncommitted changes since the last commit

         git diff

-   Comparing files between two different commits

         git diff sha1 sha2

-   Comparing two branches

    ```bash
    # the diff input is the tips of both branches
    git diff branch1..other-feature-branch
    git diff branch1 other-feature-branch

    # the three dot operator
    git diff branch1...other-feature-branch
    ```

    The three dot operator initiates the diff by changing the first input parameter `branch1`. It **changes `branch1` into a ref of the _shared common ancestor commit_ between the two diff inputs**, the shared ancestor of branch1 and other-feature-branch. The last parameter input parameter remains unchanged as the tip of other-feature-branch.

-   Comparing files from two branches

         git diff master new_branch ./diff_test.txt

-  Comparing working directory with staging area

        git diff


-  Comparing staging area with repository

        gir diff --staged
