# [Autocorrect for simple typos](https://nathanhoad.net/git-autocorrect-for-simple-typos)

    gitty(master)$ git config --global help.autocorrect 1
    gitty(master)$ git stats
    WARNING: You called a Git command named 'stats', which does not exist.
    Continuing under the assumption that you meant 'status'
    in 0.1 seconds automatically...
    On branch master
    Your branch is up-to-date with 'origin/master'.
    nothing to commit, working tree clean

# [Atom](https://atom.io/) Editor Setup

    git config --global core.editor "atom --wait"

# Basic configuration

    # makes sure that Git output is colored
    git config --global color.ui auto

    # displays the original state in a conflict
    git config --global merge.conflictstyle diff3

    git config --list
