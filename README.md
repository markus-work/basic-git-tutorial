# Welcome to the basic Git tutorial

Install git by following the instructions for your operating system [here](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git)

## Getting started

### Create repository

Open a terminal and navigate to the folder you want to create the repository in.

`cd <path-to-folder>`

Create a folder there and enter it:

`mkdir <folder-name>`

`cd <folder-name>`

Then initialize the repository:

`git init`

### Make a change and commit it

Find the folder in the file explorer and add a README text file.
When we write

`git status`

we can see that the file is untracked. type:

`git add README.txt`

to stage the file. "Write the lego instructions for it"

`git status`

shows us that the file is now green

`git commit` 

This will open a text editor, and you will need to write a message to describe why you made the change and then save it.
Then git will commit it and gives it a hash. "Stores all the instructions in a booklet"

> TEXT EDITOR HELP. You may be in a new type of editor called vim.
To write here, type `i` to be start writing the message.
Then hit `esc` to exit the insert mode. type `:wq` to save and quit.
dfgdfsg
Type `git status` to see that no changes are there.

This process can be repeated a lot. People usually commit too seldom. This can be done very often. It is better with too many commits than too few, as it is easier to combine them later, rather than splitting them up.


### Pushing it


After you have done some more changes to the source code/README file, and committed this, you can push it.
Always push your work after a work session, so that other people can get hold of it.

Normally this can be done with

`git push`

but the first time you have to set the remote("cloud destination") of where to push to. "What cloud to upload to."

For that we need to create the project/repository in the cloud. Go to the [github](https://github.com/) and create a new repository and fill in the name(refered to as `<repo-name>`). You can leave everything else as is.
After creating the repository, look for the url that will look like `https://github.com/<your username>/<repo-name>.git` and copy it(referred to as `<url-to-repo>`)

Go back to the termial and add the remote. Remember to paste in the url to the repository.

`git remote add origin <url-to-repo>`

This will add a remote that is called `origin`, which points to the repository to the cloud.

We then need to establish that there is a branch called `master` ("a shelf") where we want to place the commits("instruction books") and push to it.

`git push --set-upstream origin master`

When you refresh the project page, you will see that your README file is now visible.
For later pushes on the same branch, you only need to type `git push`

>Cloning
To be able to download someone elses repository, you can write `git clone https://github.com/<username>/<repo-name>.git`. Then you can do the same git commands.

### Creating a new branch
When implementing a new feature, you normally create a new branch so that you don't disturb anyone else and you can easily revert if something goes wrong. Type

`git branch`

to see the available branches and the star indicates which branch you are on.

`git checkout -b <new-branch-name>` 

creates a new branch called `<new-branch-name>` and switches to it. It is the `-b` that signifies that you are creating a new branch. Type

`git branch`

to see that you have created a new branch and switched to it(by looking at the star). Type 

`git checkout master`

to switch back to the original branch. `git branch` will then show you that you are on master. However we want to go to the new branch and make a change, so type

`git checkout <new-branch-name>`

And commit some changes(like swapping out some words) to the readme file and push it to the new branch. Again we now need to say that there is a new branch in the cloud that we want to push to. This is only done once for each new branch.

`git push --set-upstream origin <new-branch-name>`

### Merging

Meanwhile, your partner(user2) continues on the master branch. They will do some other changes in the same location in the readme file(swapping the same words for other words). Make sure they call `git branch` so they know that they are doing changes to the correct branch commit and push this to master. 

When both have made the changes, committed them, and pushed them, it is time to merge the two branches together.

`git fetch`

gets all the updates from the cloud, on other branches as well.

`git branch`

should show the branch created by user1. change to the branch with

`git checkout <new-branch-name>`

and type

`git pull`

to update the branch. Then switch back to the master branch by typing

`git checkout master`

Then we want to merge the changes into master by typing

`git merge <new-branch-name>`

And there will (hopefully) be a conflict. You will need to resolve this in a code editor and then stage and commit it. For more details look at [these instructions](https://support.atlassian.com/bitbucket-cloud/docs/resolve-merge-conflicts/) from point 5 to 7.

## Pull requests

We will have push restrictions on master branches, so that you can't push to the master branches. So to be able to merge new changes into branches by create merge requests.

Merge requests enable other users to review the code and leave comments to improve the code before merging.

Start by creating a new branch, and make some changes to it
Then push it to the cloud. Go into the repository page, and click on `PUll Request` in the sidebar.
Click on `New Pull Request` and select the source branch.
This is the branch that has the new changes.
The target branch is the branch you want to make changes to.
Click `Compare branches and continue`.
Write a title and description.
Here you describe why you want to change, and what areas are of special interest and request feedback for.
You can then click `Submit pull request`.

Now the merge request is available for others to see and comment.
The other partner can try out commenting the changes.
They can also add commits to the same branch and the merge request can be updated.

When all the comments are resolved, you can merge the request and the changes will appear in the target branch.

# Learning More

To get more familiar with branching, you can go to these sites:

## Guided git branching
https://learngitbranching.js.org/

## Free explore
https://git-school.github.io/visualizing-git/

## Navigation page for git resources
https://try.github.io/

