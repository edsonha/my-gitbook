# GIT

To put the files in the unstaged area:

```
$ git add -N
```

To review the changes before moving the files from unstaged to staged area:

```
$ git add -p
```

To create a new branch and switch to the branch:

```
$ git checkout -b "x-branch"
```

To check out what branch is available:

```
$ git branch
```

To switch branch:

```
$ git checkout "x-branch"
```

To push to the new branch:

```
$ git push origin "x-branch"
```

Git Branch Strategy

```text
If your commit in your branch is old against master branch
git checkout master
git pull master
git checkout "your branch"
git rebase master
git push --force 
```

