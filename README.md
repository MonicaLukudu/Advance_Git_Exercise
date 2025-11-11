# Advanced git commands
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