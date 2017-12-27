---
published: true
layout: post
---
## Git resources

[Git and GitHub](http://r-pkgs.had.co.nz/git.html#git). 

from R packages by Hadley Wickham

[How to Use Git and GitHub](https://classroom.udacity.com/courses/ud775/lessons/2980038599/concepts/29607789240923)


[git intro](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001373962845513aefd77a99f4145f0a2c7a7ca057e7570000)

[Git Course at DataCamp](https://campus.datacamp.com/courses/introduction-to-git-for-data-science/basic-workflow?ex=10)

### How can I view a repository's history?
The command git log is used to view the log of the project's history. Log entries are shown most recent first, and look like this:

commit 0430705487381195993bac9c21512ccfb511056d
Author: Rep Loop <repl@datacamp.com>
Date:   Wed Sep 20 13:42:26 2017 +0000

    Added year to report title.
The commit line displays a unique ID for the commit called a hash; we will explore these further in the next chapter. The other lines tell you who made the change, when, and what log message they wrote for the change.

When you run git log, Git automatically uses a pager to show one screen of output at a time. Press the space bar to go down a page or the 'q' key to quit.

You are in the directory dental, which is a Git repository. Use a single Git command to view the repository's history. What is the message on the very first entry in the log (which is displayed last)?


## How can I view a specific file's history?
A project's entire log can be overwhelming, so it's often useful to inspect only the changes to particular files or directories. You can do this using git log path, where path is the path to a specific file or directory. The log for a file shows changes made to that file; the log for a directory shows when files were added or deleted in that directory, rather than when the contents of the directory's files were changed.

You have been put in the dental repository. Use git log to display only the changes made to data/southern.csv. How many have there been?

### How do I write a better log message?
Writing a one-line log message with git commit -m "message"is good enough for very small changes, but your collaborators (including your future self) will appreciate more information. If you run git commit without -m "message", Git launches a text editor with a template like this:

    # Please enter the commit message for your changes. Lines starting
    # with '#' will be ignored, and an empty message aborts the commit.
    # On branch master
    # Your branch is up-to-date with 'origin/master'.
    #
    # Changes to be committed:
    #       modified:   skynet.R
    #
The lines starting with # are comments, and won't be saved. (They are there to remind you what you are supposed to do and what files you have changed.) Your message should go at the top, and may be as long and as detailed as you want.