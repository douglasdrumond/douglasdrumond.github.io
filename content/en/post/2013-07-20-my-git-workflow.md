---
author: Douglas Drumond
featured_image: /assets/images/cover.jpg
categories: ""
date: "2013-07-20T00:00:00Z"
tags:
- git
title: My Git Workflow
---

Proceeding with my sequence of posts about version control systems, I’ll
explain my Git workflow. It’s quite simple, after set up, the day to day
workflow is as follows:  
1. get the latest information from remote server: `git pull --ff-only`  
2. create a new branch and switch to it: `git checkout -b branch_name`  
3. work, work, work, then commit: `git commit`  
4. go back to master: `git checkout master`  
5. check if there’s something new: `git pull --ff-only`  
6. merge my work back into master: `git rebase branch_name`  
7. upload the modifications to server: `git push`  

And since I reached the magic number
[seven](http://en.wikipedia.org/wiki/The_Magical_Number_Seven,_Plus_or_Minus_Two),
those are the seven steps.

## Set up

During the rest of this article, I’m supposing you’re using git from command
line and it’s a Unix-like operating system (Mac OS X **is** Unix and Linux is
Unix-like) and you know basic command line stuff, such as `cd`, `ls` and `pwd`.

### Once for a lifetime

The first thing you need to do after installing git is letting it know who you
are:

    git config --global user.name "John Doe"
    git config --global user.email "john.doe@example.com"

Of course, replace the values with your real name and e-mail. What do these
lines do? Git uses a special file called `.gitconfig` that lives in your home
directory. That is just a plain text file with several lines in the format `key
= value` grouped into `[sections]`. You can edit it in a plain text editor such
as Vim, Sublime Text 2, Gedit and so on. That file stores your global
configuration, i.e., configuration you want to use everywhere. There’s
a similar file called `config` inside the project’s `.git` directory that
stores the configuration for that specific project. If two configurations
overlap, the per project one is used. So, above two lines put these in your
`.gitconfig` file:

    [user]
        name = John Doe
        email = john.doe@example.com

Later I’ll show these values in action.

### Once per project

There are two ways here: you’re creating the project from scratch, or you’re
downloading the code from someone else’s repository, I’m considering the
latter, so, let’s download the repository:

    git clone git://example.com/path/to/project.git

That’ll create a directory called `project` inside current directory where the
command was called from. `cd` into it and you’re ready for the work loop.

## The work loop

Now that you’re in your working mode, just do the five steps from the beginning
of this text. Let’s dig into them, but not so much, just enough to justify
them.

* `git branch`

This isn’t really needed, it just to certify where you are. You should see
something like

    * master
      other-branch

Probably just `master`, if you recently cloned the repository. Even if there
are other branches, make sure that master has an asterisk beside it. If it
doesn’t, do `git checkout master` and check `git branch` again.

* `git pull --ff-only`

This is used to get the latest information from the remote server. If you just
cloned it, you can skip it for now, but if you’re working in a team, do this so
you avoid headaches later. Well, it doesn’t hurt, do it and commit it to muscle
memory. Why `--ff-only`? So you won’t create merge bubbles, I’ll explain them
in a later post.

* `git checkout -b branch_name`

This will create a new branch called *branch name* and switch to it. It’s
a shortcut for

    git branch branch_name
    git checkout branch_name

While not strictly necessary, it’s good for your sanity when trying to merge
things later if someone uploads new code while you’re working on yours. Replace
*branch_name* with the name you want. I usually put what kind of work I’ll do,
for instance, `git checkout -b user_login` when working on the login feature.

* Time to work, then `git commit`

Now it’s the time to work. Edit your HTML, style it with your CSS, write your
Go server code, your fancy Rails site, your amazing Ruby program, your Python
script, do whatever you need. When you reach a milestone, commit it to the
repository. You don’t need to commit it just when you’re ready to upload, you
can do several small commits. For instance, suppose you’re refactoring some
code and changed a method, but with just this change, the software breaks (you
need to modify something in another class). Well, you can commit this right
away since it’s just in your local repo. This way, if you screw something
later, you can rollback to this point easily and redo the screwed part. Think
of these commits as save points in a videogame. Later, when you finish the
level and kill the boss, you can squash the save points into one big *level
clear* commit before uploading it to the remote repository.

Here I cheated, there are two commands: first you must add the files you want
to commit with `git add`. Then you can commit them with `git commit`.
Alternatively, you can use `git commit -a`, but explicitly adding provides much
finer control over what you’re committing. For instance, if your editor creates
temporary files, with *commit -a* you’re putting them into version control as
well. There are ways to deal with this, but let’s keep it simple for now.

When you call `git commit`, an editor will pop up for you to write a commit
message. This message should describe what you just have done. Good commit
messages are descriptive. Keep the first line short and direct, the second line
must be blank and write freely from the third line to describe the work. Lines
starting with hash sign (#) are skipped. Which editor will open is governed by
`GIT_EDITOR` environment variable.

Now that you finished working, let’s see if someone worked on something while
you were doing your stuff.

* `git checkout master`

Now you’re back to master branch, where our main development lives.

* Check if there’s something new: `git pull --ff-only`

This is the same as step one above, it brings new code from the remote repository.

* Put your work back into master: `git rebase branch_name`

There are two ways to put your work back into master, either by rebasing or
merging. The final result may look the same, but they have different meanings
and do different things behind the curtains. Since the created branch is just
a private branch, just do `git rebase` as stated, I’ll explain the differences
in a later post.

* upload the modifications to server: `git push`

Finally, upload your changes so other developers on your team can see it.

## Troubleshooting

When pulling or pushing, if the repository isn’t correctly set, git may
complain. Just read the error message, it’s usually tells what must be done to
fix it. For instance, maybe `git pull` doesn’t know where to pull from, and
shows you this message

    There is no tracking information for the current branch.
    Please specify which branch you want to merge with.
    See git-pull(1) for details

        git pull <remote> <branch>

    If you wish to set tracking information for this branch you can do so with:

        git branch --set-upstream-to=origin/<branch> master

Just do what it just told you and configure your master branch to track from
the remote master:

        git branch --set-upstream-to=origin/master master

If it’s while pushing, git may show this:

    fatal: The current branch bla has no upstream branch.
    To push the current branch and set the remote as upstream, use

        git push --set-upstream origin master

Just do what it tells:

    git push --set-upstream origin master

and don’t be bothered again.

In later posts I’ll explain how git works, so these commands will become
clearer. Also, this is my workflow, it’s not the only way to work. Adapt it to
suit your style or needs.

