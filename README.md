# git3d
should help with doing three-way diffs and merges when using git

traing repo: https://github.com/github/platform-samples.git
to do: merge from add-shell-scripts to master

```
cmd> git3d show-trees add-shell-scripts
base_tree_id:    b3348e3
source_tree_id:  a627d7a  (origin/add-shell-scripts, add-shell-scripts)
target_tree_id:  f591871  (HEAD -> master, origin/master, origin/HEAD)
```

```
cmd> git3d checkout-trees add-shell-scripts
getting base tree
getting source tree
base tree: /var/tmp/git3w-trees/asmirnov/BASE--b3348e33f0b81d40b6bc25baaed078daa039c771
source tree: /var/tmp/git3w-trees/asmirnov/SOURCE--a627d7a05f9cb447d96f0e1e218d24215bf42a2d
```
