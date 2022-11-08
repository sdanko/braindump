# Git Merge

There are two modes of merge operation:
- Fast Forward merge
- Three-way merge

**Fast Forward** merge happens when there is a linear path between branches you want to merge. There will be no new commit and destination branch will just point to the latest commit of the source branch.

**Three-way** merge happens when there is no linear path to the target branch. This merge causes an extra commit to tie together the two branches. This commit will have parents in two branches that were merged.

Resources:
- https://medium.com/mindorks/understanding-git-merge-git-rebase-88e2afd42671
