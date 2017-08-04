=====
Lab 3
=====

Welcome to the final SSXG Course Lab!

This lab will teach you how to collaborate on Git code with others in a real-time example. You will master the art of collaborating on a GitHub-hosted repository through the **centralized workflow**. You will also learn to resolve **merge conflicts** and **pull requests**.


--------
Overview
--------

By the end of lab 3, you will:

- Have a good understanding of **merge conflicts** and **pull requests**
- Have practical experience using all of the Git tools we've learned so far in a real-world example
- Master the **centralized workflow**
- Be ready to host and contribute to collaborative repositories on GitHub!


--------------
Homework Recap
--------------

There was no pre-lab homework this week!

Any questions on Git, GitHub or anything we've discussed or practiced in the course so far before we begin?


----------------------------
The Merge Conflict Revisited
----------------------------

Recall from lab 2 that a **merge conflict** can arise if the same line in two branches have been changed. This can also happen if a file was changed in one branch and deleted from another. In either case, since Git does not assume which changes are correct, we need to decide which change to keep.

Resolving a **merge conflict** generally happens in 4 steps:

1) Identify the files that are in conflict (Git conveniently does this step for us).

2) Choose the version of each conflicted file to keep. Git adds text to the conflicted files to indicate which lines need to be resolved. You can then open the files, see the conflicts, and decide which to keep (in the practice section, we will look at a tool that helps with this step).

3) Once the conflicts are resolved, stage the desired files with **git** add <resolved-files>.

4) Finally, continue with the merge using **git** merge --continue. This will proceed with the merge and - barring missed conflicts - commit the merge to the Git history.

If ever are in **merge conflict** mode and want to abort the merge, returning to before you attempted it, you can use:

	**git** merge --abort


-------------
Pull Requests
-------------

When it comes time to push your changes to a shared GitHub repository, it can be helpful to notify your collaborators about your proposed changes before you make them. To do this, we use a **pull request**. A **pull reuest** is a *request* that you make to your collabortors to *pull* your changes into their code. This gives them the opportunity to see your commits, make comments, or even make commits of their own to ensure that your changes are merged smoothly.

**Pull requests** are handled through GitHub. In the practice, we will see that starting one is as easy as selecting the branch with your changes, selecting the target branch, and adding some comments for your collaborators. Once the **pull request** is created, all collaborators *with commit access* to the target branch will automatically be notified of your request.


-----------------------
Putting it All Together
-----------------------

You now have all of the background that you need to work on your code in parallel with collaborators. To give a quick recap, here is an example of the first cycle of work on a collaborative Git project.



--------
Practice
--------

The aim of this lab will be to practice all of the tools we have learned so far to contribute to a open source repository on GitHub. The project you will contribute to is.... *this one*! 

As always, first, let's open a terminal window and navigate to where you want to place the repository, say:

	**cd** /Users/christian/Desktop

Now clone the `SSXG git course <https://github.com/cjtu/SSXG-git-course>`_ by typing:

	**git** clone https://github.com/cjtu/SSXG-git-course.git

Let's cd into the lab 3 folder:

	**cd** SSXG-git-course/lab3

Before we start development, let's make a branch off the master. Name it like so:

	**git** branch -b ""

To initiate a **pull request**, we follow the instructions from `Creating a Pull Request <https://help.github.com/articles/creating-a-pull-request/>`_ on GitHub:

.. image:: create_pull_request.png

