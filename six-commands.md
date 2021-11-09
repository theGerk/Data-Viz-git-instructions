# git concepts


## commit
A commit is the smallest unit that git keeps track of. I think of it as a "version" of your project. Each time you make a commit that is a place you could go back to at any time in the future. All commits are save perminantly in the git history.

## branch
A branch allows you to have multiple different versions of your project in the same repo. This allows for multiple, possibly conflicting changes, to be made at the same time without issue. Branches keep track of all the changes (commits) made on them, and whenever you like you can update one branch with changes from another. This process of updating is called merging.

## local/remote
Git doesn't have to be used with a remote repo, but it has some really nice built in features to make it easy. When working with a git repo you always work on a local copy, changes can be synced bentween a remote and local copy by pushing and pulling.

## Bonus feature: Pull request
Pull requests (PR for short) are a common feature built into git hosting services like GitHub. We aren't going to use it for the project but its worth knowing about it as its a life saver on larger teams. Basically a PR allows you to ask to allow your branch to be merged into another branch. These can get fancy, having built in automated tests and having forced checks from QA and the team lead before changes are allowed to go into specified branches. We're just going to be merging our branches as its simpler.

# The six git commands you'll need in college

- `git add .` or `git add -A`
- `git commit -m "<message>"`
- `git push`
- `git pull`
- `git checkout <branch_name>` and `git checkout -b <branch_name>`
- `git merge <branch_name>`

## `git add`, `git commit`, and `git push`
---  
`git add` tells git what changes should be included in the next commit. `git add .` tells git to add everything in the current folder to the next commit, `git add -A` tells git to just add everything to the next commit.

`git commit` tells git to make a new commit on your current branch. Use `git commit -m "<messege>"` as all commits need a message.

`git push` tells git to share the current state of the branch you're on with github. This will have github's copy of the branch get all the commits you've made since you last pushed on this branch.


Techincally you don't need to do these three commands together, there really isn't any reason not to do it. Doing this more often is better. I try to do it at least every time I switch focus or finish a "thing".


## `git pull`
---
Sometimes github has changes that you don't have locally. This can often happen when two people are working on the same branch (which we won't be doing for the project) or if you switch which computer your working on. This will also happen when you need changes from a branch someone else has been working on. This will just pull all the changes (commits) for the current branch's remote version into your local.

## `git checkout`
---
This is how we deal with branching. You can see all branches you have by running `git branch`, but checkout is how we actually switch branches. the command is `git checkout <branch_name>` to switch to an already existing branch or `git checkout -b <branch_name>` to switch to a new branch you make then. Be careful that you've commited before you checkout, not doing so will cause headaches. Be aware that when you create a branch that branch will be coming off whichever branch you are currently in.

## `git merge`
---
This command allows us to get one branch up to date with another's changes.

If I run `git merge foo` while on the branch `bar` then I will update `bar` branch with changes from `foo`. The directionality can be difficult to remember on this, but the trick is you only ever change the branch you are currently on.


## Bonus commands `git status`
---
This is super helpful when figuring out what things look like right now. It gives you all sorts of useful information, but doesn't actually do anything. Try it out as often as you like!

## Bonus Bonus `git help <from a TA>`
---
Feel free to ask us questions when something isn't working like you think it should with git.
