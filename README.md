# Gitting started

One member of your team is going to create a repo on GitHub. This person is your git master and will have additional responsibilities. Your going to have GitHub generate a `.gitignore` for Python. Next you're going to need to add every other team member as a collaborator. You can find this under `Settings -> Manage access -> Add people`.

Now before everyone starts cloning one person should clone the repo to fix the `.gitignore` a bit. Specifically we want to add the following line: `.DS_Store`. The following commands will do this for you:
```
git clone <url>
cd <repo>
echo ".DS_Store" >> .gitignore
git add .gitignore
git commit -m "fixing .gitignore"
git push
```
Make sure to replace `<url>` with the url GitHub gives you to clone and `<repo>` with the repo's name.

Now you'll have a nearly empty repo on GitHub that everyone has access to. You're ready to start working.

## Cloning

Now everyone can clone the repo with `git clone <url>`.

# Branches are your friend

Now your ready to start working with your group. Theres more than one valid git workflow. I'm going to lay out a workflow that I think is the best for our projects.

## Structure

The main branch is where completed tasks live. Each task in progress will have its own branch (potentially more, if you find it helpful). No branch should have multiple people working on it at a time. If two people are working on the same thing then either only one is making code changes or there is a branch for each person working on the task. An example repo might look something like the following.

branch | description
--|--
`main` | This is where all completed work lives.
`feature/setup-api-calls` | This where David is working on getting the API calls working. *In this case David is the only person writing code for this task.*
`feature/cleaning-data-inputs` | We have multiple people working on this task so we're going to use this as a sort of master copy for this work.
`feature/cleaning-data-inputs/benji` | Here's where Benji's making his contributions to this.
`feature/cleaning-data-inputs/stephen` | Here's where Stephen's making his contributions to this.
`stretch/automated-email-list` | Here's where Farshad went of on a tanget and started making an automated email list. This probably won't make it into the final project but its good work and we don't want to throw it away. Maybe we'll finish it and include it in the end.

## Using the structure

First, I'm going to go into my git repo and open a terminal. Lets say I want to start work on my ##finish this sentence

# Examples

The following instructions all assume you're in the local git repo.

---

### Making a commit
We've been doing this for a while now.
```
git add -A
git commit -m "<some message here>"
git push
```
The push is not strictly required, but no reason not to do it.

### Important to do before switching branches
**Make sure you don't switch branches with uncommitted work!** Anytime, before you do a `git checkout` command (which we will be seeing a lot of in the following examples) you should **always** check that you do not have uncommitted work. You can check to see if you have uncommitted work by running
```
git status
```
and if you see: 
```
nothing to commit, working tree clean
```
then you are good. If you do have uncommited work, then you need to either commit the changes or undo the changes before branching.

---

### Starting work on a new task.

```
git checkout main
git checkout -b <new_branch_name>
git push --set-upstream origin <new_branch_name>
```

### Starting 


##Good start. I would state later on that `git checkout -b <branch>` is only used the first time. Every subsequent checkout of the existing branch is `git checkout <branch>`