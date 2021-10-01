# git3d
should help with doing three-way diffs and merges when using git

Suppose you need to do merge where your current git tree will be the target (where you put new changes at).
You also know the source git branch (or commit, tag).

Then you can start using git3d to see what exactly you are going to merge:

```
git show-trees origin/main

```



it is still require polishing but main use-case works:
 - go to checkout git directory - it is target
 - find suitable identification of source commit. it could be origin/main
 - use git3d show-trees <source-tree-id>
 - when you ready do
