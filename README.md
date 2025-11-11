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