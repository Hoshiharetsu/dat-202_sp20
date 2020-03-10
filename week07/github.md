# How to GitHub

## One person, one repo, multiple machines, not worrying about branches yet

(I'll draw the model on the board now. I'm also going to go through all of these steps with you, in person.)

1. Log in to your own GitHub account, on github.com, and create a new repository. For our purposes, let's call it `github_practice`. Check the box to "Initialize this repository with a README". (You'll be able to delete this after we're done tonight if you want!)
1. In Git Bash, navigate to a directory where it makes sense to have some GitHub repositories. My suggested command on Windows, especially on the school machines:
	* `cd /c/Users/[username]/Documents`
1. Clone your repository to your machine. The command you'll type (type all of it except the URL, don't just copy/paste) in Git Bash is
	* `git clone https://github.com/[username]/github_practice.git`
	* this will make a directory inside your current working directory; to do anything else, you'll have to navigate into that directory (`cd github_practice`) 
1. Open the README in whatever editor you like, and change it. Give it a friendlier title than the repository name, and feel free to add other text if you like. For future reference, [this is the Markdown cheat sheet I like to use](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet). Save your file when you're finished.
1. Go back to Git Bash, and check the status of your repository.
	* `git status`
	* there should be at least one file that needs to be added
1. Add the file you want to track, in this case, README.md.
	* `git add README.md`
	* this isn't best practice, but you'll often see me use `git add *` which adds EVERYTHING - I kind of make up for it by typing `git status` all the time, so I do know what I'm adding
1. Commit your changes.
	* `git commit -m "Added some text to README"` 
	* your commit message (the part in quotes) can be anything, including a set of emojis; if you're GitHubbing alone, you can do what you want, but if you're working with others, it's best to use the commit message to communicate what actually changed
	* if you leave off the -m tag, you can leave a much longer commit message, in whatever editor is the default for the bash shell you're using
1. Push your changes up from your local repo to the repo on the cloud (in GitHub).
	* `git push origin master` 
	* this is the default incantation for pushing to a remote repository, but we'll learn how and when it will change in a few minutes
	* `origin` is the identifier of the remote repository
	* `master` is the name of the branch you're working on
1. Feel free to go see the changes in GitHub.
1. Now **change machines.** If you're on a laptop, log in to the school's machine. If you're on a school machine, go to a different school machine. (Leave the other machine logged in; you'll be back in a couple of minutes.)
1. Clone the repository from GitHub on the new machine, and navigate into the directory housing your local repo on that machine.
1. Create a file; you can do this directly from Git Bash by typing `touch trashfile.txt`
1. Add the file to the files tracked on Git, commit your changes, and push. 
1. Go back to your first machine. (Leave the new machine logged in; you'll be back.) Check the status of the repository with `git status` - oh no, you're behind by one commit! 
	* `git pull origin master`
	* now you have pulled the changes from the remote repository to your local one - if you go look, your new file is in that directory!
1. Do we want to practice making changes and swapping machines a couple more times, to really hammer that skill in, or are we feeling good? Once we're feeling good we will move on to...

## One person, one repo, multiple branches

You might recall from the reading that sometimes&mdash;especially when we're working on a multi-person team, but even sometimes when we're working alone&mdash;we want to work on more than one feature at once, without any risk that we damage our core (hopefully fully tested) functionality. We can segment our work by using branches.

1.  Make sure you've got everything pulled onto your local repository from your remote repository (on GitHub) with another `git status` and/or `git pull origin master`
1. We only have one branch, named `master` right now. Prove it to ourselves:
	* `git branch`
1. Let's make another, named `feature1` (feature one, not feature L)
	* `git branch feature1`
1. Let's see which branch we're currently on (ok, Git Bash helps us out with this, but go ahead and check anyway)
	* `git branch`
1. OK, we're still on `master`, no big deal, but let's go ahead and get on our feature branch
	* `git checkout feature1`
1. Make a change. In fact, go ahead and add a whole new file, to make it easy to see where which changes are sitting. 
1. Add the file to be tracked, and commit it just like you normally would. 
1. The thing that changes is our push statement:
	* `git add origin feature1`
1. Now go look at the repository in GitHub. Whoa, branches!
1. OK, now go switch computers again. Now you need to get access to the remote's branches on this other machine, right?
	* `git fetch --all`
1. Now your machine at least knows about the other branch(es), though if you type `git branch` you probably still only have `master` on this machine. So let's check out our feature branch:
	* `git checkout feature`
	* now you should get a message like "Branch 'feature1' set up to track remote branch 'feature1' from 'origin'."
	* this next bit is probably unnecessary (it was for me when I tested it), but just in case...
	* `git pull origin feature1`
1. Make a change. Add, commit, and push -- what is our incantation for this push?
1. Go back to your other machine. What is the incantation to pull the changes?
1. Now, you can use [git merge](https://www.atlassian.com/git/tutorials/using-branches/git-merge) to merge your branches, and that's actually totally OK. But that isn't what Eric had you do in [week 6](https://technologyrediscovery.net/python/cit129_courseCalendar_sp20_fresh.html), so it's not what I'm going to have you do this time. We'll do this his (equally good) way and do a Pull Request.
1. Go to the repository on GitHub. You'll be offered the option to make a Pull Request. Do it. Since you are also the owner of the repository, you'll also be able to merge the pull request (a second button). Do that too.
1. Once `feature1` has been merged into `master`, you can pull the changes onto your local master branch (on either machine):
	* `git checkout master`
	* `git pull origin master` - this grabs the changes to the master branch after your pull request on the cloud
	* `git branch -d feature1` - this removes the feature1 branch

## TODO: fork, add remote, make changes round-robin, and the git rm command

## About .gitignore

Ever used a Mac or looked at the repo of [someone who used a Mac](https://github.com/csheldonhess/citizen-weed-warriors) and seen that annoying .DS_Store file show up?

More importantly: have you ever had a private API key that you probably clicked something and agreed you wouldn't share with the world? (Let's make a pretend one, shall we?) Go ahead and type the following: 
	* `touch api-key.txt`

Situations like the ones above are why we have .gitignore.

First, you have to create it (make sure you're in the top directory of your github_practice repo):
	* `touch .gitignore`

Then you want to put in whatever files you want it to ignore. Since a file that starts with a period is hidden from Windows and MacOS by default, the easiest thing for us to do is edit it in the CLI:
	* `nano .gitignore`

And then literally just type "api-key.txt" (without the quotation marks) and hit ctrl-x and enter to save. 

Let's test it:
* `git add *`
* `git commit -m "added gitignore"`
* `git push origin master`

And let's go see what shows up on the public repo!