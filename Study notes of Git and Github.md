## Git and GitHub
* Git, a version control system, which was created in 2005 by Linus Torvalds.
* In Git terminology, these user-created checkpoints are called commits. Commits are the basic building blocks of Git, each one representing a version of the content at one point in time. Git requires the user to supply commit message each time a commit is created.
* Each commit has an ID, an author, a date, and a message associated with it.
* The message explains what has changed since the last commit.
* The ID is sort of like a serial number. It uniquely identifies each commit and lets you refer to it. Can check what changes a commit introduced by using the git diff command.
* Git diff is similar to the FC or diff program, but instead of just comparing two files, it can compare different versions of a file within git.
##### How Often to Commit
> A good rule of thumb is to make one commit per logical change. 
> For example, if you fixed a typo, then fixed a bug in a separate part of the file, you should use one commit for each change since they are logically separate.
> If you do this, each commit will have one purpose that can be easily understood.
> Git allows you to write a short message explaining what was changed in each commit, and that message will be more useful if each commit has a single logical change.
- - -
* GitHub, a code sharing and collaboration plateform.
> Git ia local. GitHub is where we share and collaborate with other people.
>
> GitHub is a website that makes it easy to share an entire git repository with other people.
> 
> GitHub lets you suggest changes and send them back to the creator of the project.
- - -

##### Some Commands
* git init
> Initializes or creates a new Git repository.
> Git doesn't any commits when you create the repository.
* git status
> git status is a command you like to run frequently, because it shows which files have changed since the last commit.
* git add
> git add file_name
> This command will to add files to the staging area
* git log --stat
> This command will give some statistics about which files have changed in each commit.
* git config --global color.ui auto
> This command will to get colored diff output.
>
> The git config command just changes settings in Git and the --global flag means that it will apply to all of your Git projects and not only this one.
* git checkout id
> Temporarily change files back to how they were at the time of any commit. It's sort of like restoring a previous version.
>
> git checkout != SVN checkout, git checkout is not the same thing as a SVN checkout. In git, checking out a commit means resetting all of your files to how they were at the time that commit was made.
> 
> Why would you want to check out a previous version of your code ?
> Maybe one reason is, if a bug was introduced, but you're not sure which commit introduced it. You can test wether a commit has the bug by checking out that commit and running the code.
> 
* git diff
> git diff with no arguments compares the working directory to the staging area. git diff --staged compares the staging area to commit which it the most recent commit. git diff commit1 commit2 compares commit1 to commit2.
>
> git diff id1 id2 will compare two commits of repository.
>
> git diff without id will compare the files of working directory and staging area. This will show any changes you've made that you haven't added to the staging area yet.
>
> git diff --staged : view the difference between the staging area and the most recent commit(repository)
* git reset --hard
> Discard any changes in either the working directory or the staging area.
> If run this command, can't get these changes back.

* git branch
> create and view branches.
> git branch with no arguments will show you current branches.
> git branch branch_name(with argument), creates a new branch with that name.
* git log --graph --oneline branch_name1 branch_name2
> Visualize the branch structure
>
> --oneline, make the output shorter and easier to see.
* git merge branch1 branch2 or git merge branch
> Since the two branches are merged, the order in which they are typed into the command line does not matter. The key is to remember that git merge always merges all the specified branches into the currently checked out branch, creating a new commit for that branch.
* git show commit_id
> Compare a commit to its parent.
* git branch -d branch_name
> d stands for delete, delete branch_name. This won't delete the commits in the branch, it will only delete the label.
* git remote
> View and create remotes.
>
> git remote add a_name_you_want_use a_URL_for_your_remote
> Add the repository on GitHub as a remote, run command, git remote add a_name_you_want_use a_URL_for_your_remote, you can use any name here and it's the name that you'll use within this repository, to refer to the repository on GitHub.
> If you only have one remote, it's standard to name it origin.
>
> git remote -v
> V stands for verbose, and means that git remote will output more information.
* git push origin(the remote) master(local branch)
> git push take two arguments. The remote you want to send changes to, and the name of the local branch that you'd like to push.
* git pull origin(the remote) master
> git pull like git push, need to specify the remote, also need to specify the branch you want to pull, which is the master branch on the remote.
>
> Pull takes a branch from a remote and brings it to your local repository.
> And push does the opposite, taking a branch and pushing it to a remote.
>
> What really happens when you pull a branch?
> 
> This is exactly what happens when you do a git pull.
> 
> First, the remote branch gets fetched, updating the local copy of the remote branch. Then, that branch gets merged into the local one. So git pull is the same as git fetch followed by git merge.
>
> git pull origin master = git fetch origin + git merge master origin/master
>
* git fetch
> Using git fetch update the local copy of the remote branch.


* Fast-Forward Merges
> Fast-Forward merge occurs when you merge two commits, where one is ancestor of the other. That is, where one commit is reachable by the other. 
>
> For example, if you can reach branch A from branch B, then merging B into A would be a fast-forward merge.
>
> Remember, the only criteria for whether something would be a fast-forward merge is if the branch you are merging into is an ancestor of the branch that you're merging from.

* git log origin/master or git diff origin/master master
> Inspect the local copies.
* Forking a Repository
> Forking a repository allows you to make a copy of somebody else's repository directly on the GitHub servers without pulling down the code to your local machine first.
>
> You can fork an existing repository and have it appear under your own account with just a single click. Then to make your modifications, you'd likely want to pull down the code onto your own machine, unless the files are simple enough to edit directly on GitHub.
>
> Forking is a lot like cloning. In fact, a fork is just a clone that GitHub makes for you on their own machines.
>
> Few other side effects to forking:
>
> Like GitHub keeping track of the number of people who've made forks on your repository.
> And the forks all linking back to the original.
> It also makes it easier to suggest changes back to the original repository.

* pull requests : a feature of GitHub

* * *
##### Git Errors and Warnings Solution
* Should not be doing an octopus
> Octopus is a strategy Git uses to combine many different versions of code together. This message can appear if you try to use this strategy in an inappropriate situation.

* You are in 'detached HEAD' state
> HEAD is what Git calls the commit you are currently on. You can “detach” the HEAD by switching to a previous commit, which we’ll see in the next video. Despite what it sounds like, it’s actually not a bad thing to detach the HEAD. Git just warns you so that you’ll realize you’re doing it.

* Panic! (the 'impossible' happened)
> This is a real error message, but it’s not output by Git. Instead it’s output by GHC, the compiler for a programming language called Haskell. It’s reserved for particularly surprising errors!

* Merge Conflict(Newline characters between Windows and Unix systems)
> "Enter" key on the keyboard, on Unix systems(Mac OS or Linux), it's "line feed" character or LF or \n; on Windows systems, it is two characters, "carriage return" and "line feed" or CRLF or \r\n.
>
> To fix this, Windows users should set the global autocrlf attribute to true:
> git config --global core.autocrlf true.

* git add confict_file_name and committing
> Let git know that the conflict was resolved.


## Some Version Control Systems
* Saving manual copies
* Dropbox
* Google Docs
* Wikipedia

##### Feature Comparison Chart
|               | Any Editor | Use Offline | Manual Save |
|---------------|:----------:|:-----------:|:-----------:|
| Manual Saving |    Yes     |     Yes     |     Yes     |
|    Dropbox    |    Yes     |     No      |     No      |
|  Google Docs  |    No      |     No      |     No      |
|   Wikipedia   |    No      |     No      |     Yes     |
|      Git      |    Yes     |     Yes     |     Yes     |
|      SVN      |    Yes     |     No      |     Yes     |
