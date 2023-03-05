# git3d

should help with doing three-way diffs and merges when using git

# what is 'git merge'?

Merge is the process of creating new git commit out of available ones. Most important case is the merge of two commits - **source** and **target**. When you issue command like `git merge main` you specify **source commit** as cmd line argument - `main` branch in this case. **target** commit is the head of the local branch on the tree where your current directory is now - use `git branch --show-current` to find out.

The rest of merge processing will include two steps:
* step 1: deciding on how merge commit result will look like
* step 2: merge commit creation using merge result from previous step


## Merge step 1
The are many ways to arrive the result of merge. You may decide to modify your **target commit** manually - possibly using some fragments from **source**. It can be done with the help of two-way diff&merge tools.<br/>
If you trust the algo you may try to generate merge result using `git merge` command. In either way you will arrive to local modifications of **target commit** - this is your **merge result**.

Depending on the way how you use git you may be given a chance to look at **merge result** before merge process moves to its second step. But one thing you should realize - `git merge` command in its default configuration will not leave you such chance - it will create **merge commit** without telling you anything special about that. If you have problem with such optimistic approad you may try to use command like `git merge --no-commit`. In this case you will be able to complete your merge later using `git commit` (?is it true - need to refresh my memory)

## Merge step 2: merge commit creation using merge result from Step 1

**merge commit** is created using **merge result** which is usual git working tree with modifications. 
You may just use `git commit` command to create new commit. However in this case information about origin of **source** will be lost. <br/>
Better way is to create git commit where you specify **source** as additional parent of your **merge commit** - in addition to **target** which is always the parent. This kind of commits with multiple parents are created by `git merge`


# how git3d helps me if i need to do merge?

`git3d` utility is trying to help if you decided that automatic merge with immediate commit or two-way merge is not something you want. 

`git3d` workflow cleanly separates between **merge result** preparation phase and subsequent creation of **merge commit**.
`git3d` give you chance to to prepare **merge result** using three-way diff&merge tools like `kdiff3`. 
After you prepared to continue with achieved **merge result** `git3d` have the way to create **merge commit** in the manner as `git` itself creates that.

So `git3d` allows you to stop using `git merge` completely. Many of us find it beneficial in some important situations when merge process itself is not something you want to trust to automatic algo or require some additional changes or actions to be made during merge preparation phase.


## git3d workflow


traing repo: https://github.com/github/platform-samples.git
to do: merge from add-shell-scripts to master

```
cmd> git3d show-trees add-shell-scripts
base_tree_id:    b3348e3
source_tree_id:  a627d7a  (origin/add-shell-scripts, add-shell-scripts)
target_tree_id:  f591871  (HEAD -> master, origin/master, origin/HEAD)
```

```
cmd> git3d download-trees add-shell-scripts
getting base tree
getting source tree
base tree: /var/tmp/git3w-trees/asmirnov/BASE--b3348e33f0b81d40b6bc25baaed078daa039c771
source tree: /var/tmp/git3w-trees/asmirnov/SOURCE--a627d7a05f9cb447d96f0e1e218d24215bf42a2d
```
