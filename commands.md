# git log
```bash
git log --oneline
git log --stat
git log --patch == git log -p  == git show
```
```bash
git log --oneline --graph --decorate
```
## [Filtering the Commit History](https://www.atlassian.com/git/tutorials/git-log)
 * By Amount
   ```bash
   git log -3
   ```
 * By Date

 To display all the commits added between July 1st, 2014 and July 4th, 2014, you would use the following:
 ```bash
 git log --after="2014-7-1" --before="2014-7-4"
 ```
 * By Author

 The following command searches for commits by either Mary or John
 ```bash
 git log --author="John\|Mary"
 ```
 * By Message

 For example, if your team includes relevant issue numbers in each commit message, you can use something like the following to pull out all of the commits related to that issue (you can also pass in the -i parameter to git log to make it ignore case differences while pattern matching):
 ```bash
 git log -i --grep="JRA-224:"
 ```
 * By File

 For example, the following returns all commits that affected either the foo.py or the bar.py file (the -- parameter is used to tell git log that subsequent arguments are file paths and not branch names):
 ```bash
 git log -- foo.py bar.py
 ```
 * By Content

 If you want to know when the string Hello, World! was added to any file in the project, you would use the following command:
 ```bash
 git log -S"Hello, World!"
 git log -G"<regex>"
 ```
 * By Range

 You can pass a range of commits to git log to show only the commits contained in that range.
 ```bash
git log <since>..<until>
git log master..feature
 ```
 * Merges
 ```bash
 git log --no-merges
 git log --merges
 ```
