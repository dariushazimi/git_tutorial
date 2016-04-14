# git_tutorial
Info on Git from commandline

	git log
	git show
	git status

	git clone https://github.com/dariushazimi/git_tutorial.git anyName_OR_let it blank
	git remote -v # list of remote repos
	git remote add origin https://github.com/dariushazimi/git_tutorial.git

Lets push everything up to the remote repo
	git push -u origin master —tags #-u updates, —tags:pushes all the tags to the remote repo


## Revert changes from staging to working area

	git reset HEAD README.md


## Revert changes back
git checkout -- README.md

## Setup your editor
	git config core.editor "mate -w"
	git config --global -e

## Git History and Alias

	git log --oneline --graph --decorate --all

- Just type git log and compare it with the line of above.
- online: allows us to combine the lines
- graph: provides an astrick based graph denoting our branching higharchy
- decorate: tells us with commits are part of which branches and other lables
	within the git repo
- all provides the history for all the commits available in this repo

We can create an alias for this

	git config --global alias.hist "log --oneline --graph --decorate --all"

to use it now just type
	git hist
	git hist -- filename

Look at your git config file
	git config --global --list

	git add -u # to update git after changes such as move a file to a new file name

	git add -A # make all modification possible on to current working directory and add it to git index

#Ignore files
Create a .gitignore file
Include *.log and or any other pattern you want to exclude

#Comparing differnt commits
as an example we run the git hist and we see something like this:
* 56e2b25 (HEAD -> master) added gitignore
* 25cabf1 Ignoring files with git
* d9772b1 (origin/master, origin/HEAD) Cleaned up Readme
* 1d2d466 Nothing added, cleaned
* 889cf06 Removed git_command line file
* ed59c80 deleting demo file
* 89dd901 Git command line tips
* 8cdba8e Added new commands for history and alias
* aff70a2 Added basic commands to get started with Git
* b3044b7 Initial commit

to compare one of the commits with the head:
	git diff 8cdba8e HEAD

or use the difftool command
	git difftool 8cdba8e HEAD

#Branching
Juat a time line of a commit.

keep in mind HEAD points to the last commit of the branch.

##Which Branch
	git branch

##New Branch
While working on changes if you decide that these changes should be really part of a new
branch you can do the following by createing a new branch.
Lets create a new branch called updates
	git checkout -b updates


To see the changes and differences between updates and master branch run the following:

	git diff updates master

To integrate the changes from updates to master
We need to change to master

	git checkout master

	git hist

	-merge changes from updates branch to master

	git merge updates

To see the changes and differences between updates and master branch run the following:
	git diff updates master

##Fastforward
What is git fastforwad? When changes are so simple, git will do a fast forward, meaning we will
pretend that we never moved away from the master.
Once the changes are done we can delete the branch

	git branch -d updates
	The above command does not remove the history, it just removes the label.

##Conflict resolution
	git branch -a # to see our branches


## Links
* http://www.gitguys.com/topics/merging-with-a-gui/
* https://git-scm.com/docs/pretty-formats
* http://www.emoji-cheat-sheet.com
* http://www.gitguys.com/topics/

### books

 https://git-scm.com/book/en/v2
### terminal
https://github.com/mdo/ocean-terminal
https://github.com/fabianperez/ocean-dark-iterm

### Useful Bits

To print the name of your currently checked out branch in your prompt, include this line as part of your PS1:

'git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/''

#### Extras

A few people also asked about @patrickmckenna's Terminal.app theme. He uses ocean-terminal. His PS1 (prompt) is

'export PS1="\[\$(tput bold)\]\[\$(tput setaf 6)\]\w\[\$(tput setaf 3)\]\$(git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/ (\1)/')\[\$(tput setaf 6)\] > \[\$(tput sgr0)\]"'


### Learn markdown
 <http://commonmark.org/>

# Git Tags
Marking major milestones

Set a label or tag
	git tag mytag
	git tag -d mytag

	git tag -a v1.0 -m “Release  1.0”
	git tag —list

	git show v1.0

#Git Stashing - Save temporary changes

	git stash
Lets say we are working on something and realize that we should be doing that right now.
We should have been in another branch or work on something else. We can use git stash
git stash list

next

	git commit -am “notes”
Now to apply our stash

	git stash pop # will apply the changes to or orginal file prior to the stash
	git stash list # will show that there is nothing in our stash


#git reset, git reflog


	git reset number —soft (the least distractive of all)
	git reset number --hard
	git reflog

#p4merge mergtool, diff.tool

To setup p4merge on mac

	git config —global diff.tool p4merge
to set the path

	git config —global difftool.p4merge.path /Applications/p4merge.app/Contents/MacOS
disable the prompt so that you are not constantly prompted

	git config —global difftool.prompt false

Lets set up the merge tool as well.

	git config —global merge.tool p4merge
	git config —global mergetool.p4merge.path /Applications/p4merge.app/Contents/MacOS

to list our config

	git config —global —list
	git config —global -e # to load it in our default text editor
