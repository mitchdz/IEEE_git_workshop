# Advanced git commands


## Adding all deleted files to staging
```bash
$ git ls-files --deleted | xargs git add
```
This command will stage all the deleted files for you so you don't have to add them one by one. Let's do an example.

```bash
$ for i in {1..15}; do touch TEST${i}.txt; done
$ git add TEST*
$ git commit -s -m "add TEST files"
$ rm TEST*
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes not staged for commit:
  (use "git add/rm <file>..." to update what will be committed)
  (use "git restore <file>..." to discard changes in working directory)
        deleted:    TEST1.txt
        deleted:    TEST10.txt
        deleted:    TEST11.txt
        deleted:    TEST12.txt
        deleted:    TEST13.txt
        deleted:    TEST14.txt
        deleted:    TEST15.txt
        deleted:    TEST2.txt
        deleted:    TEST3.txt
        deleted:    TEST4.txt
        deleted:    TEST5.txt
        deleted:    TEST6.txt
        deleted:    TEST7.txt
        deleted:    TEST8.txt
        deleted:    TEST9.txt
```

You could do `git add TEST*` and that will stage the file deletions, but sometimes the files all have different names and you can't conveniently glob them. Well you can use the trick at the start to add all deleted files to staging

```bash
$ git ls-files --deleted | xargs git add
$ git status
On branch main
Your branch is ahead of 'origin/main' by 1 commit.
  (use "git push" to publish your local commits)

Changes to be committed:
  (use "git restore --staged <file>..." to unstage)
        deleted:    TEST1.txt
        deleted:    TEST10.txt
        deleted:    TEST11.txt
        deleted:    TEST12.txt
        deleted:    TEST13.txt
        deleted:    TEST14.txt
        deleted:    TEST15.txt
        deleted:    TEST2.txt
        deleted:    TEST3.txt
        deleted:    TEST4.txt
        deleted:    TEST5.txt
        deleted:    TEST6.txt
        deleted:    TEST7.txt
        deleted:    TEST8.txt
        deleted:    TEST9.txt
```
