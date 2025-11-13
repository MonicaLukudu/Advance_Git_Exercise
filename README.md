# Advanced git commands (Part 1)
## 1. Missing file fix (using amend)
<!-- this commands are used after it being staged(a point before the commit using "git add #filename" )-->
### git commit --amend -m "" <!-- this is to commit the missing file to the last commit -->
### git log --oneline <!-- this is to check on the changes the has been done on the last commit-->

## 2. Editing commit history (using rebase)
### git log --oneline <!--this is to check the number of commits you have and target the commit you want to change-->
### git rebase -i HEAD~2 <!--this is where you can access the commits that you displayed from the above command and press i to edit the commit you want to edit (that's by replacing the pick keyword with reword then save and exit (you can save by clicking on "Esc", colon, then type "wq" and press "Enter")) modify the commit as you please then save and exit-->
### git log <!-- to check the edited commit-->

## 3. Keeping History Tidy - Squashing Commits
### git log --oneline
### git rebase -i HEAD~4 <!--this is where you can access the commits that you displayed from the above command and press i to edit the commit you want to edit (that's by replacing the pick keyword with squash then save and exit (you can save by clicking on "Esc", colon, then type "wq" and press "Enter")) modify the commit as you please then save and exit-->

## 4. Splitting a commit
### git rebase -i HEAD~4
### git log --oneline
### git reset HEAD^ <!--You can use 'git reset HEAD~' OR 'git reset ID'-->
### git rebase --continue <!--this is to show that it is completely rebased and updated-->
### git add fileName <!--this is to stage the files separately-->
### git commit -m "" <!--this is to commit the files separately-->

## 5. Advanced Squashing
### git rebase -i HEAD~3 <!--to display the last three commits and while in the editor, select the commit you want to squash by replacing the pick with "s" or "squash" and move to the next editor to delete the old commit and replace it this the new messgage-->
### git log --oneline <!--to check the changes made-->

## 6. Dropping a commit
### git rebase -i <!--in the rebase editor choose one of the commands that is "drop" or "d" to remove the unnecessary commits from the tracking history-->

## 7. Reordering commits
### git rebase -i <!--all you need to do is cut and paste the commit to the dersired place-->
<!--although this can be confilcting because you may end up having marging conflict that you will have to fix manually-->

## 8. Cherry-picking commit
### git switch -c ft/branch
### git add test5.md
### git commit -m "Implement test 5"
### git log --oneline <!--Use this to identify the commit you want to cherry pick and copy the ID mof the commit-->
### git switch main
### git cherry-pick <ID> <!--after switching to the main branch oyu can cherry pick it and the commit will be in the main branch-->
### git log --oneline

## 9. Visualizing Commit History
### git log --graph <!--The git log --graph command is used for visualizing commit history, providing an ASCII graph that illustrates branching and merging to clarify a repository's complex workflow. This helps in understanding the relationship between commits and branches at a glance.-->

## 10. Understanding Reflogs (bouns)
### git reflog <!--The git reflog command, on the other hand, tracks the local history of your Git operations (like branch switches, resets, and merges), not the commits themselves. It acts as a safety net, allowing you to recover lost commits or navigate back to previous states of your repository, even after destructive actions like a hard reset.-->

# BRanching Basics (Part 2)
## 1. Feature Branch Creation
### git switch -c ft/new/new-feature

## 2. Working on a new feature
### touch feature.txt
### git add feature.txt
### git commit -m "Implemented core functionality for new feature"

## 3. Switching Back and making more changes
### git switch main
### tocuh readme.txt
### git add readme.txt
### git commit -m "Update project readme"

## 4. Local vs. Remote Branches
### Remote branches are references on your local machine that represent the state of branches stored on a shared Git hosting platform, such as GitHub. These branches, typically named like origin/main, are read-only markers that allow developers to coordinate their work. To keep your local branches synchronized with the remote, you use $\mathbf{git \ push}$ to upload your committed changes to the remote repository, and $\mathbf{git \ pull}$ to automatically fetch and integrate changes made by others from the remote repository into your local branch. This push-and-pull mechanism ensures that all collaborators are working from the latest, unified version of the project.

## 5. Deleting a branch
### git branch <!--this is to check the branches availablity and the current branch it is in.-->
### git branch -D 


## NOTE
### Lowercase 'd': for Safe Delete. The lowercase -d is an alias for --delete.
### It will only delete the local branch if its commits have been fully merged into the branch you are currently on.

### Uppercase 'D': it Force Delete. The uppercase -D is an alias for --delete --force.
### It forces the deletion of the local branch regardless of its merged status.

## 6. Creating a Branch from a Commit
### git checkout -b ft/new-branch-from-commit HEAD~2 <!--this is to create a new branch and move the commits of your desire to that branch and move their-->

## 7. Branch Merging
### git checkout main
### git merge ft/new-branch-from-commit
### in case you get a merge conflict, manually fix it.

## 8. Branch Rebasing
### git checkout ft/new-branch-from-commit
### git rebase main
### git add <conflicted-file-name>
### git rebase --continue
### git checkout main
### git merge ft/new-branch-from-commit

## 9. Renaming a Branch
### git branch -m ft/new-branch-from-commit ft/improved-branch-name <!--this changes the branch name from the current one to a new one-->
<!--'-M' a flag frequently seen in the mv command (move/rename) it is used to rename a branch, while '-m' is a short hand of a '-messge' that is used to commit a message. -->

## 10. Checking Out Datched HEAD
### git checkout <commit-hash> <!--this command help taking you back to the specific commit that was done by that time-->

# Advanced Workflows PART 3
## 1. Stashing Changes
### git stash <!--this command temporarily saves youe staged and unstaged changes in the file, and then reverts your wirking directory to the state of the last commit-->

## 2. Retrieving stashed changes
### git stash pop <!--this command is used to remove the changes from the stash list-->

## 3. Branch Merging Conflicts
### To resolve merge confilcts manually through the text editor, click on the changes that is done and merge the comparison that is provided then click on the complete.

## 4. Resolving ,erge conflicts with a merge tool
### I case you don't have merge.tool configured in your laptop, use this command: git config --global merge.tool code
### git merge <branch-name> <!--this is to merge the branch you want to merge. -->
### git mergetool
### File will be displced when you run the git mergetool command on the terminal:
### *on the top-left this is the local file that you wnat to merge with, *on the top-middle this is the base file before any changes were made in both branches. *on the top-right this is the remote file that you want to merege with the file in the top-left * and the file on the botton is the one that is going to show the changes that need to be marged.
### once you have identified the changes you need to edit, by remmoving the >>>> HEAD and all the other unnecessary lines and remove the line you want to replace the changes then click Shift Z a couple of times and quit the rest one by one then add and commit your work and you will automatically leave the mergetool editor.

## 5. Understanding the DETACHED HEAD state
### The "detached HEAD" state in Git is a valid, though unusual, state where the special pointer HEAD (which normally points to the tip of your current branch) is pointing directly to a specific commit.
### In simple words, the detached HEAD state means you're in "view-only" mode and are not on a branch.

## 6. Ignoring Files/Directories
### the '.gitignore' file is a powerful file configaration file used to tell git which files and directories to intentionally ignore and not track in the repository.
### to avoid the temporary files from being tracked, add /tmp in the file to ignore a directory anmed tmp located only in the root of the repository.

## 7. Working with Tags
### Git tag are like permenent, static bookmarks in your repositoryhistory. They are primarily used to marfk specific points as important, unlike branches, tags don't change or move once they've been created.
### - To create a tag: 'git tag v1.0'(it will traget the last commit in the log) or 'git tag -a v1.0 -m "Initial release version"(this one here is for a commit that is staged)
### - To checkout tag version: 'git checkout v1.0' ( this checks out commit pointed to by v1.0. but this only puts you in a detached HEAD state as you are not on the branch.) and to return: 'git checkout main'(To go back to active development, you must check out a branch)

## 8. Listing and deleting Tags
### To delete the Local Tag: 'git tag -d v1.0' and to delete the remote Tag: 'git push origin --delete v1.0'
### - To list and view tags: 'git tag'(to list) and 'git show v1.0' (displays infomstion about the specific tag name provided.)

## 9. Pushing Local Work to Remote Repositories
### git push origin <branch-name> <!-- but before pushing make sure to pull to check out for any chancges in the remote repositories by using this command "git pull"-->
### - To push tags[note the defult 'git push' command does not send the tags to the remote repository.]: 'git push origin v1.0'(pushes a single tag named v1.0 to the remote repository.) and 'git push origin --tags' (pushes all of your local tags to the remote repository.)

## 10. Pulling Changes from REmote Repositories
### using the 'git pull' command to pull the changes in the remote repository and resolve it manually or using the merge tool command 'git mergetool'.