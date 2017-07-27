=====
Lab 1
=====

Welcome to the second SSXG Git Course lab! This lab will teach you where Git shines: in collaborating with others! After learning a simple sequence of steps and commands in Git, you never have to wonder if those little changes you made will break everyone else's work.... but even if they do, you'll know what to do about it! 


--------
Overview
--------

By the end of lab 2, you will:

- Have a good understanding of how to set up and take part in a shared research project
- Understand why Git is referred to as a "**Distributed** Version Control System" (**DVCS**)
- Master the  fundamental git commands *branch* and *merge*
- Work with remotes using *remote*, *clone*, *fetch*, *push*, and *pull*


--------------
Homework Recap 
--------------

In the pre-lab homework you learned the basic cmoands for working with branches and remotes in Git. Some commands you should recognize are:

- git branch
- git merge
- git remote
- git clone
- git fetch
- git push

Any questions on the pre-lab homework before we begin?


---------------------------
The Tree of Lif- er - Git
---------------------------



-------------------
Where's the Remote?
-------------------

Last time we said that Git is a Version Control System (**VCS**), but to be more specific, it is a *Distributed* Version Control System, or **DVCS**. A **DVCS** is a **VCS** that is fully distributed to each system that it exists on. Where you may checkout snapshots of files when using other **VCSs**, with a *DVCS** you copy the entire repository. This means that if one server fails, any other existing repository can fully restore it. Pretty neat (more reading on **VCS** types `here <https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control>`_).

What does this mean for maintaining a workflow with collaborators through Git? Basically, it means that you have options. In this lab I will show you **one** way of working with others in Git, but it is by no means the only way. I believe the **centralized workflow** will be the simplest for our numbers and purposes (and it avoids learning about `benevolent dictators and lieutenants etc etc <https://git-scm.com/book/en/v2/Distributed-Git-Distributed-Workflows>`_).

The *centralized workflow* is summed up in this image:

.. image:: centralized_workflow.png

In it, each *developer* has a **clone** of a **remote** *shared repository* as a *local repository* on their system. To make changes, the *developer* can **pull** the most up-to-date version of the *shared repository* into their local repository, **commit** their changes locally, **fetch** changes from the *shared repository* in case it changed while they were working, **merge** their changes locally, and finally **push** their changes to the *shared repository*.

Easy right? There's a lot going on and we'll go into each step in depth in the practice, but first we need ask: "where's the remote?"

There are several options available for hosting Git projects "in the cloud", and each has different strengths (here is a whole `list of websites <https://www.git-tower.com/blog/git-hosting-services-compared/>`_ with descriptions). You could also set up a repository on a private internal server as your *shared repository* (remember, in a **DVCS** no one repository is special), but hosting your repository online gives you a few advantages:

1) You have access to your repository, anytime, anywhere, on any device (any device with Git, maybe not your smart toaster)

2) Many websites have useful GUIs (Graphical User Interfaces) for browsing your repository, your commit history, checking collaborators, or managing *Pull Requests* (more on that later)

3) Already having your code, commit history, and documentation online ensures that **when you're ready**, you can release your code to the wider scientific community or to the public to do more transparent, productive, and reproducible science

I'll stop beating around the bush, I know you all want to hear about `GitHub <https://github.com/>`_. GitHub is a ridiculously large Git repository hosting service that was started about 10 years ago and now hosts over `63 millions projects from over 23 million people <https://github.com/about>`_. Needless to say it is the largest code hosting service ever and has somehow continued to be a free service for people to share, colloborate on, and open source their code. I'm not endorsing it as the best place to host your code, but it is the most recognized service and is very simple to use.


--------
Practice
--------
Here we will practice branching, merging and working with remotes. Recall the commands we know so far and feel free to refer back to them here:

- **git init** creates a new Git repository.
- **git status** inspects the contents of the working directory and staging area.
- **git add** adds files from the working directory to the staging area.
- **git diff** shows the difference between the working directory and the staging area.
- **git commit** permanently stores file changes from the staging area in the repository.
- **git log** shows a list of all previous commits.
- **git checkout HEAD** discards changes in the working directory.
- **git reset HEAD** unstages file changes in the staging area.
- **git reset SHA** Resets to a previous commit in your commit history.



^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Lab 2a - Branching and Merging
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Lab 2b - Working with Remotes
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^




Open a shell window. Navigate to your Documents folder using the **cd** (change directory) command. You can type out the full path or navigate one folder at a time. The **ls** (list contents) will list the files and directorires in your current directory and is often helpful for navigating the shell. 

Create a new folder called *lab1* in your Documents using *mkdir* ("make directory"):

	**mkdir** lab1

Enter your new directory using **cd**. Let's tell Git to track our directory:

	**git** init

You should see a confirmation message "Initialized empty Git repository". You can check that the *.git* folder was created using:

	**ls** -all

Now we can start coding. In your favourite text editor, create the file *script1.py* with the following Python function::

|def HelloWorld():
|    """
|    """
|    print("Hello World")

Make sure to save the file to your lab1 directory. Now lets head back to the shell and see what Git thinks of our new file:

	**git** status

In the summary, we can see that *script1.py* is untracked. Let's add it to the *staging area* with:

	**git** add script1.py

Now that it is staged, let's make our first commit to the git repository. Don't forget to always leave a useful commit message with the -m flag. Messages should be present tense with enough info to remember what changed in this commit:

	**git** commit -m "Add my message to this commit"

Now return to your text editor and make two new files, *data1.txt* and *data2.txt*. You can write whatever you like in the files. Now let's check the status of the repository again:

	**git** status 

Let's say we do not want git to keep track of our data files until we find some real data. It's fine to leave them untracked in the lab1 directory, but the *Untracked files* notifications may get tiresome. To tell git to exclude specific files, we can create a *.gitignore* file in the repository. This can be done from the shell with::

|	"> .gitignore"

Or in command line with::

|	"cd. >.gitignore"

Now open up the *.gitignore* file and either add the two data files by name on separate lines, or use the wildcard character (\*) to exclude all text files with the single line::

|	"\*.txt"

Now add and commit your *.gitignore* to your git repository. Check that the text files are gone by checking the status of the repository yet again (you will probably do this often):

	**git** status

Now return to *script1.py* and define a second function *GoodbyeWorld* that prints "Goodbye World" so that the file looks like::

|def HelloWorld():
|    """
|    """
|    print('Hello World')
|
|def GoodbyeWorld():
|    """
|    """
|    print('Goodbye World')

Save the file, then add your changes to the staging area. Before you commit, you remember you wanted to document your functions. Return to *script1.py* and fill in your empty docstrings. Remember that docstrings, like commit messages, should also be present tense and imperative. Now *script1.py* could look something like this::

|def HelloWorld():
|    """
|    Print Hello World  
|    """
|    print('Hello World')
|
|def GoodbyeWorld():
|    """
|    Print Goodbye World
|    """
|    print('Goodbye World')	

If we check git status now, we see that script1.py is still staged from before, but now it also has unstaged changes. Let's say you want to check the difference between **your current directory and the last commit**, you can use the command:

	**git** diff

If you ever get stuck in a *diff* or *log* command in the shell, type "q".

But this doesn't show the changes you have already staged. To see the difference between your **staged changes and the last commit**, you can use the --cached flag:

	**git** diff --cached

This is a good place to pause and make sure you understand what happens when you stage files, and what differences the "**git** diff" and "**git** diff --cached" are showing you. If you need to, you can discard all the changes to *script1.py* and return to just after we comitted the *.gitignore* using:

	**git** reset HEAD

THis discards the changes in the staging areas. Then to revert *script1.py* to the way it was at the last commit:

	**git** checkout script1.py" 

Then you can work through the changes to *script1.py* again starting with adding the GoodbyeWorld function, just to ensure that you know which changes went into the staging area. If you feel comfortable with the staged and unstaged changes to *script1.py*, we can move on to how we will commit them.

Here, we have a couple options. For one, we could unstage everything in the staging area using "**git** reset HEAD" and then stage and commit *script1.py* with the up to date changes. A shorter way of accomplishing this is simply running **git add script1.py** to stage the most recent changes to script1.py. This would result in the same commit as in option 1. 

A third option is to store our changes as two separate commits. The trick to making the most out of Git is to have deliberate commits and useful commit messages. At the end of the day (or month, or year), your commits will be your only snapshots of your project. Let's first commit the changes we already had staged:

	**git** commit -m "Add GoodbyeWorld function"

You can check with "**git** diff" that only the documentation changes need to be committed now (WARNING: Here's is a quick but dangerous shortcut that will simultaneously **add** AND **commit** all modified or untracked files in the directory, skipping the staging area. Use with caution and always know what you're committing!):

	**git** commit -a -m "Add documentation to HelloWorld and GoodbyeWorld"

Now we can look at the log and see the commit history of lab1:

	**git** log

Here is where your commit messages shine! You can see the unique commit ID, the author name and email you set at the beginning, the date and time, and the useful commit message for each commit we made. The log command has some useful flags to make the output more pretty... The --pretty flag for instance:

	**git** log --pretty=oneline

We can filter log output too. Try:

	**git** log -n 3

Or:

	**git** log --since="1 month ago" --until="10 minutes ago"

If you're still lost with your detailed commit messages and want to find where a certain insertion of deletion happened, you can use the -p flag to see the full *diff* between each commit:

	**git** log -p

Congratulations for making it through Lab 1!


-----
Recap
-----

In this lab you learned:

- How Git stores and keeps track of your files over time
- How to track a directory with Git using git init
- How to track new files or stage modified files with git add
- How to commit changes and write useful messages with git commit
- How to check the status of your repository with git status
- How to track differences in your repository or staging area with git diff
- How to get a detailed (or pretty) history of the repository's commits with git log

Next week, we will get to the meat of why Git is perfect for team projects when we talk about branching, merging, and remote repositories!