## Initial Setup:

Download & Install git bash: https://git-scm.com/downloads

(optionally during installation disable git GUI and select Notepad or any desired text editor if you aren't familiar with vim)

Download & Install git lfs: https://git-lfs.com

Open git bash in desired project location or navigate to desired project location using `cd` command and clone the project:
```
git clone http://104.248.239.8:3000/SOW/SOW.git
```
For a first time, it will ask for credentials.

## Git guide:

### Use of git bash:

Navigate to project folder using file explorer
Rightclick on empty space and select "Git Bash here"

### Useful Git commands:

#### Status
This command shows untracked and unstaged files in **Red** and staged files in **Green**. Displays your changes.
```
git status
```

#### Branch
This displays local branches, Creates and Deltes specified branches:
```
git branch
git branch ExampleBranch
git branch -D ExampleBranch
```

#### Checkout
This command switches branch you are standing on, to a specified branch. Used only for local branch branches.
```
git checkout ExampleBranch
```

#### Switch
This command switches branch you are standing on, to a specified branch, but for **remote** branch. It's useful when you want to see/add to changes of other developer that hasn't merged their branch to **Development**
```
git switch ExampleBranch
```

#### Log
This command shows commits log. You can use it to checkout old commit from its **SHA**.
```
git log
git log --oneline
git checkout 7af4bd831abe3104fe33d488c66642959ae67fc9
```

### Uploading / Pushing commands:

#### Add
This adds your local changes to branch you are standing on as indexed files. **.** means to add every change.
It will change files from *git status* from **Red** to **Green**, that means all the files that were unstaged or untracked are now staged.
```
git add .
git add /Content/ExampleFile.uasset
```

#### Commit
This commits staged files. -m is needed to specify commit message. Type link to jira ticket in the beginning.
```
git commit -m "https://spoilsofwar.atlassian.net/browse/SOWDEV-585 | Example commit message"
```

#### Push
This command uploads branch from your local repository to remote. Use `--set-upstream` or shorter `-u`.
```
git push --set-upstream origin ExampleBranch
```

#### restore
This command will restore specified file/files. With staged files you'll need to add prefix `--staged` to include them as well.
```
git restore .
git restore /Content/ExampleFile.uasset
git restore --staged /Content/ExampleFile.uasset
```

#### reset (advanced)
This command resets your commit, turns commit into untracked and unindexed files. HEAD^ resets last commit, HEAD^2 resets 2 commits in past **Use with caution and supervision if necessary!**
```
git reset HEAD^
git reset HEAD~2
```
### Downloading / Pulling commands:

#### Fetch
This command gets/updates remote branches, gets references to newely created branches from other developers. `--all` downloads all changes without this you would need to specify branch to download from. `--prune` cleans up outdated branches.
```
git fetch --all --prune
```

#### Pull
This command downloads changes on branch you are standing on.
```
git pull
```

#### Rebase
This command will update files on branch you are standing from specified branch. It will cause conflict if changes on specified branch has changes that your branch has. Good way to check if you have conflict with main branch.
```
git rebase Development
```

### LFS Commands

#### lfs lock
This command locks file, after doing this others won't be able to push changes to this file.
```
git lock /Content/ExampleFile.uasset
```

#### lfs unlock
This command unlocks file.
```
git unlock /Content/ExampleFile.uasset
git unlock .
```

#### lfs locks
This shows locked files from other developers.
```
git lfs locks
```
