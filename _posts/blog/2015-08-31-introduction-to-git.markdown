---
layout: post
title: Introduction to Git
date: 2015-08-31T19:10:00.000Z
author: Ryan Beckett
categories:
  - Source Control
  - Blog
img: gitb.jpg
thumb: git.jpg
---

Up until October 2014 I had always used a Git client for source control. Typically it would have been [SourceTree](https://www.sourcetreeapp.com) or [GitHub Desktop](https://desktop.github.com). It did the job however if i'm honest, quite often I found it difficult to understand what was happening 'under the hood'. I was able to do the fundementals; _push_, _pull_, _branch_ and _merge_ (If you don't know what these terms mean don't panic, I'll be covering some of it later) but it felt like a dumbed down version of Git. <!--more--> I often feel like this using a Git client.

![Baby playing with blocks](http://bayareafamilychildcare.com/wp-content/uploads/2012/02/baby-blocks-2.jpg)

Using Git through CLI was a lot more powerful especially when I needed more control over branching and merging. It was also useful when using services other than GitHub (which happens more than you'd think) and honestly, it just feels cool to use.

Another thing to consider is that Git clients will come and go over the years; but the CLI will always be there. Now I'm not saying GUI's are all bad, they are a great way to hide complexity from the user, but when it comes to git there isn't much complexity that makes sense to hide from the user.  

In this blog post I am going to teach the fundamentals of Git using CLI, which will allow you to use the most common git tools without need the for a Git client. In a future blog post I am going to go beyond the fundamentals and show why I prefer to use Git through the CLI instead of a client.

# History of Git
> Git is a open-source code management tool; it was created by Linus Torvalds when he was building the Linux kernel. Because of those roots, it needed to be really fast; that it is, and easy to get the hang of as well. Git allows you to work on your code with the peace of mind that everything you do is reversible. It makes it easy to experiment with new ideas in a project and not worry about breaking anything  - Source: [Easy Version Control with Git](http://code.tutsplus.com/tutorials/easy-version-control-with-git--net-7449) - Tuts+. Retrieved August 30, 2015.

# Using Git
First head over to [Git](https://git-scm.com) and download the latest release for your OS and install it.

Now open your CLI and change our directory to your project folder, for this example my folder will be on my desktop. I typed this in:

Command:

Mac:

```
cd Desktop/Super\ Secret\ Project/
```

Windows:

```
cd "Desktop\Super Secret Project"
```

Now that we are inside are project folder we can get started. We need to initialize a Git repository. We do this by simply typing in:

Command:

```
git init
```

As it's told us our 'Super Secret Project' is now an empty Git repository, great. Now it's time to learn another git command, this will be your most used git command:

Command:

```
git status
```

Let's checkout what the documentation says about "git status". If you ever need any help with Git, like all things developer related, the documentation is your best friend.

> Displays paths that have differences between the index file and the current HEAD commit, paths that have differences between the working tree and the index file, and paths in the working tree that are not tracked by Git (and are not ignored by gitignore[5]). [Git Documentation](https://git-scm.com/docs/git-status)

Let's break this down. It simply means it checks for differences between your last '_commit_' and your current changes (working directory). We will use the git status to keep monitoring the states of both the working directory and the repository. Let's now make a difference, so when we run this command it actually shows us something.

I'm going to add a .txt file called NuclearCodes to my project folder. You can do the same or call it something else. It doesn't matter. We then type "git status" again to check for differences.

If we look under 'Untracked files' we can see my "NuclearCodes.txt" appears. It also shows up in red. Either of these two things tells us this file has not been added to the '_stage_'. This means if we committed are changes now anything under Untracked files' wouldn't be '_saved_'.

Before we continue let's talk a little about this word "commit". Commit is similar to saving a file, it simply allows us to store our staged changes when we run the commit command with a message describing what we've changed. An example commit is as follows:

```
git commit -m "Added NuclearCodes.txt"
```

or

```
git commit -m "Updated READEME.txt and fixed degreesToCelsius method."
```

Now something I do need to bring to your attention is those commit messages are examples of VERY BAD commit messages, but for simplicity reasons I'm using them.

Let's now add are NuclearCodes.txt to our Stage and commit the changes so it's '_saved_'.

Commands:

```
git add NuclearCodes.txt
```

```
git commit -m "Added NuclearCodes.txt"
```

Done! Now this is all well and good, but let's think big for a minute. In a 'real' project we would have 100's if not 1000's of files and it would be **very** tedious to add all of them separately. So I'm going to show you two different ways to add multiple files with one command.

By folder:

```
git add folder1/*
```

By type:

```
git add '*.txt
```

The difference between these are; let's say we had text files outside of folder1 and inside folder2. You wanted all the text files in the project to be added regardless of their folder, you would use the 'By type' command. If you wanted only the files inside of a specfic folder to be staged regardless of their type then you would use the "By folder" command.

Now let's say our folder1 had 2 '.txt' files and 1 'banner.jpg' file. folder2 had 3 '.txt' files. Now in this example we want to add all the '.txt' files in folder1, but NOT any from folder2 and NOT the 'banner.jpg'. Neither of the above commands suit are needs. One of them adds everything inside a folder and the other adds everything by their file type. Time to fess up, I did lie a little. There is a third but it's a combination of the two and suits our needs for what we are trying to do.

```
git add folder1/*.txt
```

What this simply does is, it adds all of the .txt files in folder1 and nothing else. Now knowing this knowledge, lets get back on track.

It's time we had the remote repository so our Team can access these files. Currently they are only stored locally. Go ahead and create a new empty repository somewhere. I'm going to be using Github, feel free to use whatever you want. Now that's done, let's add it.

Command:

```
git remote add origin https://github.com/RyanBeckett/Super-Secret-Project.git
```

We have staged the changes, committed them and now we want to '_push_' these changes to our recently added remote repository. We need to '_push_' these changes to GitHub (or whatever service you have used) so that the rest of our team can access the changes we have made. We do this with the following:

Command:

```
git push -u origin master
```

The -u tells Git to remember the parameters. It tells Git that we want to push our commit(s) to the master branch. So the next time we can simply run "git push" instead of "git push -u origin master".

Finally, we are going to move onto branching. Branching allows you to create a copy of the repository from which you can then modify in parallel without affecting the '_main code_'. Commits can be done the same as above, but this time other people are able to commit changes to another branch. These changes will not affect each other since they are working from two different branches. Generally, you would see two branch types, feature branch and fix branch.
- Feature Branch: If a new feature cannot be added safely in your current development branch, then you need a another branch.
- Fix Branch: While development continues on the main product, a fix branch can be created to hold fixes.

Let's create a new branch called "clean_up". Even though I just taught you the two main reasons to use branching, I am going to use neither. We are dong this to keep this as simple and as easy to understand as possible. Enter this:

Command:

```
git branch clean_up
```

The branch has been created, but we aren't inside it. So, let's switch to this branch:

Command:

```
git checkout clean_up
```

The public have found out about the 'Super Secret Project', so let's delete everything in this branch, commit it, merge it with the main branch and then delete the "clean_up" branch. Even though in source control you can revert back to previous commits, but let's hope they don't know source control.

Commands:

```
git rm *
```

```
git push origin clean_up
```

Even though we've committed and pushed these changes, they are not in the main branch. Let's merge these changes to the main branch, delete the "clean_up" branch locally, then on GitHub (or whatever service you have used) and then push all these changes.

Commands:

```
git checkout master
```

```
git merge clean_up
```

```
git branch -d clean_up
```

```
git push origin --delete clean_up
```

```
git push
```

Git checkout allows us to switch branches, so we are simply saying switch to the master branch and then the next command says merge "clean_up" branch with our current branch, master. We then delete the "clean_up" branch locally and remotely. Finally, push all of these changes.

Ta Da! That's it. Congratulations. You now know and understand the fundamentals of Source Control using Git CLI.

Now go ahead and make your own mini project and try setting it up, staging the files, committing, removing files, pushing, branching and merging. Practice makes perfect! See if you can get a merge conflict and work out how to resolve it.

If you get stuck, keep your eyes peeled for my blog post "Git, Beyond the Fundamentals". I'll be covering merge conflicts and much more.

Thanks for reading.
