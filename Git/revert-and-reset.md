# Revert and reset

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

## Remove from the staging area

To remove from staging, we can use following command:

```git rm --cached <file_name>```

Here, we are using the rm command along with switch --cached which indicates the file to be removed from the staging or cached area.

## Remove single file from committed area

First, undo the last commit: 

```git reset HEAD^ <file_name>```

Then, undo changes:

```git restore <file_name>```

Resources:
- https://stackoverflow.com/questions/58003030/what-is-the-git-restore-command-and-what-is-the-difference-between-git-restor

