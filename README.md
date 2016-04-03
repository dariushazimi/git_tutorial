# git_tutorial
Info on Git from commandline

git log
git show
git status

#revert changes from staging to working area

git reset HEAD README.md


#revert changes back 
git checkout -- README.md

#Setup your editor
git config core.editor "mate -w"
git config --global -e

git log --oneline --graph --decorate --all
