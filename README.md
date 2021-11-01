![in case of fire](https://raw.githubusercontent.com/hendrixroa/in-case-of-fire-1/master/in_case_of_fire.png)

# Gitting started

One member of your team is going to create a repo on GitHub. This person is your git boss and will have additional responsibilities. Your going to have GitHub generate a `.gitignore` for Python. Next you're going to need to add every other team member as a collaborator. You can find this under `Settings -> Manage access -> Add people`.

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

First, I'm going to go into my git repo and open a terminal. Lets say I want to start work on a new feature (lets say `feature/something-cool`). I'm going to make sure all my work is commited before I change branches ([see](###-Making-a-commit)), then I make sure I'm on the `main` branch (`git checkout main`) and that my main branch is up to date (`git pull`). Now I can create my new branch from main `git checkout -b feature/something-cool`. Now I can start working on my feature.


Now I should be commiting as I'm working, ([see](###-Making-a-commit)), typically I try to at least make sure to do this before I take any breaks to do something else ([remember this](https://upload.wikimedia.org/wikipedia/commons/a/a7/In_case_of_fire_git_push_first.jpg)), or whenever I finish a step.

Now I'm taking a pause on my work on `feature/something-cool` and I want to look at what Farshard has been working on in `feature/webpage-list`. All I do is I make sure I've commited all my work ([see](###-Making-a-commit)), then I can run `git checkout feature/webpage-list`. Its as simple as that. When I want to go back to working on my feature I can just run `git checkout feature/something-cool` and I pop back to my branch. I shouldn't need to commit anything because I shouldn't be working on someone else's branch.

Now finally I finish something cool, or I'm not finished but I'm partially finished and I'm ready to share the part of it that I have done. All I need to do is make sure I've commited and pushed ([see](###-Making-a-commit)). Now I tell the git boss that `feature/something-cool` is ready to be merged in. Now, our git boss, Farshad will checkout my branch (`git checkout feature/something-cool`) and pull the most recent version (`git pull`), then go back to main (`git checkout main`) and merge from my branch (`git merge feature/something-cool`). Here you might run into a merge conflict. This is a great time to call a TA, if you as git boss are confident you know how to resolve it, then you can do so, but this is what the TAs are here for.


Now once I had my branch merged back to main Stephen may need some of the work I had put there to work on. If so he can update the branch he's working on with the following commands (making sure to commit first ([see](###-Making-a-commit))):
```
git checkout main
git pull
git checkout <branch_im_working_on_name>
git merge main
```
Here you might get a merge conflict, and again call a TA to help.

**Optional**: You can treat the above workflow the same way with a different main and different git boss. Consider the table of branches above and look at `feature/cleaning-data-inputs`, `feature/cleaning-data-inputs/benji` and `feature/cleaning-data-inputs/stephen`. In that case when Stephen and Benji are working on their branches, whenever they want to say they are done with a step then they'll have one of them act as the git boss and use `feature/cleaning-data-inputs` as the main. The git boss won't change between, if Benji is the git boss for `feature/cleaning-data-inputs` then he'll stay that way to save from confusion. Further when Benji and Stephen want to share something they have with the rest of the group they will first use this strategy to make sure `feature/cleaning-data-inputs` is up to where they want it to be, then the'll ask the real git boss to merge from `feature/cleaning-data-inputs` to main.

# Examples

The following instructions all assume you're in the local git repo. These are various bits taht you may find useful.

---

### Making a commit
We've been doing this for a while now.
```
git add -A
git commit -m "<some message here>"
git push
```
The push is not strictly required, but no reason not to do it. If you ever get an error while pushing, see a TA and don't feel too bad, it happens.

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

Make sure to commit first.
```
git checkout main
git checkout -b <new_branch_name> 
git push --set-upstream origin <new_branch_name>
```