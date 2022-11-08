# Git Submodules

Submodules allow you to keep a Git repository as a subdirectory of another
Git repository. This lets you clone another repository into your project and
keep your commits separate.

## Adding a Submodule

To add a new submodule you use the git submodule add command with the absolute
or relative URL of the project you would like to start tracking. For example:

```
git submodule add https://github.com/chaconinc/DbConnector
```

After this command, the new `.gitmodules` file is added. This is a configuration 
file that stores the mapping between the project’s URL and the local subdirectory you’ve pulled it into:

```
[submodule "DbConnector"]
	path = DbConnector
	url = https://github.com/chaconinc/DbConnector
```

If you have multiple submodules, you’ll have multiple entries in this file. 
It’s important to note that this file is version-controlled with your other files, 
like your `.gitignore` file.

## Cloning a Project with Submodules

When cloning a project with submodules, by default you get the directories that contain
submodules, but none of the files within them yet. 

You must run two commands: `git submodule init` to initialize your local configuration file,
and `git submodule update` to fetch all the data from that project and check out the appropriate 
commit listed in your superproject.

There is another way to do this which is a little simpler, however. If you pass `--recurse-submodules`
to the git clone command, it will automatically initialize and update each submodule in the repository, 
including nested submodules if any of the submodules in the repository have submodules themselves.

If you already cloned the project and forgot `--recurse-submodules`, you can combine the `git submodule init` and 
`git submodule update` steps by running `git submodule update --init`. To also initialize, fetch and checkout any 
nested submodules, you can use the foolproof `git submodule update --init --recursive`.

## Pulling in Upstream Changes from the Submodule Remote

If you want to check for new work in a submodule, you can go into the directory and run git fetch and git merge
the upstream branch to update the local code.

There is an easier way to do this as well, if you prefer to not manually fetch and merge in the subdirectory. 
If you run `git submodule update --remote`, Git will go into your submodules and fetch and update for you.

Git will by default try to update all of your submodules when you run `git submodule update --remote`.
If you have a lot of them, you may want to pass the name of just the submodule you want to try to update.

## Working on a Submodule

When we’ve run the git submodule update command to fetch changes from the submodule repositories, Git would
get the changes and update the files in the subdirectory but will leave the sub-repository in what’s called a 
“detached HEAD” state. This means that there is no local working branch (like master, for example) tracking changes. 
With no working branch tracking changes, that means even if you commit changes to the submodule, those changes will
quite possibly be lost the next time you run git submodule update. You have to do some extra steps if you want changes 
in a submodule to be tracked:

1. Go into submodule directory and check out a branch: `git checkout master`.
2. Tell Git what to do if you have made changes and then `git submodule update --remote` 
    pulls in new work from upstream. The options are that you can merge them into your local work,
    or you can try to rebase your local work on top of the new changes:
   - Merge: `git submodule update --remote --merge`
   - Rebase: `git submodule update --remote --rebase`

If you forget the `--rebase` or `--merge`, Git will just update the submodule to whatever is on the server and reset your
project to a detached HEAD state.

### Publishing Submodule Changes

If we commit in the main project and push it up without pushing the submodule changes up as well, other people who try to check 
out our changes are going to be in trouble since they will have no way to get the submodule changes that are depended on. 
Those changes will only exist on our local copy.

In order to make sure this doesn’t happen, you can ask Git to check that all your submodules have been pushed properly before pushing the main project.
The git push command takes the `--recurse-submodule`s argument which can be set to either `check` or `on-demand`. The `check` option will make push simply fail 
if any of the committed submodule changes haven’t been pushed. Other option, `on-demand`, will automatically push the submodules, when pushing the main project.

Resources:
- https://git-scm.com/book/en/v2/Git-Tools-Submodules
