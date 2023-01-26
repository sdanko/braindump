# Revert, Reset and Restore

## File states

File may exist in the following states:
- **Untracked** - when you first create the file, it goes in this area 
- **Staged/index** - when you use git add command on the file, it goes in this area
- **Committed** - when you use the git commit on the file, it goes in this area
- **Modified** - the file is committed but has the local changes which are not committed or staged yet.

The index has three names: index, staging area, and cache. All refer to the same thing: the place Git sticks these "copies" of each file.

## `git reset` vs `git restore` vs `git revert`

- `git revert` is about making a new commit that reverts the changes made by other commits.
- `git restore` is about restoring files in the working tree from either the index or another commit. 
  This command does not update your branch.
  The command can also be used to restore files in the index from another commit.
- `git reset` is about updating your branch, moving the tip in order to add or remove commits from the branch. 
  This operation changes the commit history.
  `git reset` can also be used to restore the index, overlapping with `git restore`.

## Using restore

To restore a file to the specific commit: 

```git restore --source <commit_id> <file_name>```

To unstage a file:

```git restore --staged <file_name>```

To revert changes that are not yet commited:

```git restore <file_name>```

## Using reset

To undo last commit:

```git reset --soft HEAD~1```

This way, we undo the last commit by preserving the changes done to the files in the index.

In order to undo the last commit and discard all changes in the working directory and index, 
execute the “git reset” command with the “–hard” option and specify the commit before HEAD (“HEAD~1”):

```git reset --hard HEAD~1```


Resources:
- https://stackoverflow.com/questions/58003030/what-is-the-git-restore-command-and-what-is-the-difference-between-git-restor
- https://www.makeuseof.com/git-reset-single-file/

