# Gitignore

Gitignore is a useful file that tells your local git to ignore certain files when staging. Often times these will be object files and other things that don't make sense to push to main. Let's explore this.

```bash
$ touch file.o
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        file.o
```

The file `file.o` is seen with git status, but if we tell git to ignore all files ending with .o by using globbing like so:

```bash
$ echo "*.o" >> .gitignore
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
```
Git will now ignore these files by default. Of course you can add them if you force it with `-f`.

The `.gitignore` file is something you can push to the repository so everyone collaborating can share a single list of files to exclude.

If you have specific files that only you will see, for example pycharm files, you can add your own exclude list in `.git/info/exclude`. This exclude file will not be commited to main, but will remain in effect for you.

the exclude file works very similar to .gitignore, except you won't see the changes to `exclude` in git status.

```bash
$ touch file.a
$ echo "*.a" >> .git/info/exclude
$ git status
On branch main
Your branch is up to date with 'origin/main'.

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        .gitignore
```
