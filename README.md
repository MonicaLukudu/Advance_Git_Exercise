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