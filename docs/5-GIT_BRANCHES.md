# Git Branches

Branches are a great way of storing code that is being worked on. Often times there will be multiple branches in a project that are being worked on simultaneously. Let's see what branches exist

```bash
$ git branch -a
* main
  remotes/origin/main
```
We can see the `*` indicating we are on main, which this is our local branch of main. We can also see remotes/origin/main which is the remote main branch.

Let's create our own branch!

```bash
$ git checkout -b mybranch
```
And rerun `git branch -a`

```bash
$ git branch -a
  main
* mybranch
  remotes/origin/main
```
We can now see that we are on a branch named `mybranch`. Let's make a new file in this branch and commit the changes to remote.

```bash
$ echo "test2" > b.txt
$ git add b.txt
$ git commit -s -m "b: init commit"
[mybranch af91a8b] b: init commit
 1 file changed, 1 insertion(+)
 create mode 100644 b.txt
$ git push
fatal: The current branch mybranch has no upstream branch.
To push the current branch and set the remote as upstream, use

    git push --set-upstream origin mybranch

To have this happen automatically for branches without a tracking
upstream, see 'push.autoSetupRemote' in 'git help config'.
```

On that last command I tried to do `git push` but I didn't set where this branch should push to. You can choose any branch, but git gives a greate hint to push to a remote branch that matches our new branch name with `git push --set-upstream origin mybranch`

```bash
$ git push --set-upstream origin mybranch
Enumerating objects: 4, done.
Counting objects: 100% (4/4), done.
Delta compression using up to 16 threads
Compressing objects: 100% (2/2), done.
Writing objects: 100% (3/3), 320 bytes | 320.00 KiB/s, done.
Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
remote:
remote: Create a pull request for 'mybranch' on GitHub by visiting:
remote:      https://github.com/mitchdz/myrepo/pull/new/mybranch
remote:
To github.com:mitchdz/myrepo.git
 * [new branch]      mybranch -> mybranch
branch 'mybranch' set up to track 'origin/mybranch'.

```
