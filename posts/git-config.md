---
title: 'Create custom shorthands for your git 😎'
date: '2020-10-22'
---

Maybe you are thinking "Oh my God more one git article..."  and yep, it is more one git article, but please stay here , this is a short article I am sure of these tricks will help you to save some time to procrastinate more... just kidding , but I'm serious... :D



![](/assets/git_capa-1-1024x653.jpeg)

### Let's start to the beginning.

In git we have a lot of powers and I will talk more about those  in future posts but now I want to show you how to configure shorthands in git common scripts to improve your speed and give more control to you!

To create shorthands we will change our configuration file with --edit flag but one thing will happen , our loved and hated VIM will be called to edit it... to avoid it to happen (sorry experts and old school devs whose love VIM) we need to change the default editor in git configuration.

### Changing it :

`git config --global core.editor code`

With this command we will use VsCode to edit our git configurations globally.

### GO GO GO

To start and create our first shortcut :

`git config --global --edit`

Remember we are using the --global flag to change our configurations globally , use can use local if you want it.

After the command above something like it will be open in your vscode :

```\[user]
email= fredd@******

name= fredd********

[core]

editor= code
```

### Talk is cheap let's do it :

first step add the tag alias in the end of file

`[alias]`

after this tag we now will put ours shortcuts

These bellow will be our commands to create shortcuts

**GIT COMMIT - GIT ADD - GIT PUSH - GIT LOG - GIT STATUS**

```
[alias]

c = !git add --all && git commit -m
```

### the command above structure is :

**c** -> the alias itself

**!** -> Is the signal to start the command

**git add --all** -> Add all files independent of  level of file (more powerful)

**&&** -> Concatenate a other command

**git commit -m** -> I think I don't need to explain that... huh ?

### NICE :D with only a short command we add all files independent of the level and commit everything like that :

`git c "shorthand git!!!"`

### WOW \o/ GO ON

the next is : 

```\[alias]
c = !git add --all && git commit -m

s = !git status -s
```

From now I will just explain little thing about the commands because the structure you already understood .(I think...)

Look simple, just a command to show the status , but with the flag -s we turn the message simple to read:

after : 

`git status`

### will show :

```
On branch master Untracked files:
  (use "git add <file>..." to include in what will be committed)

static/assets/draft.md

nothing added to commit but untracked files present (use "git add" to track)
```

Our command : 

`git s OR [git status -s]`

### Will show

`?? static/assets/draft.md`

Very easy to understand and see what you need...

### Now  , the beautiful `git log` (no no no...)

after our shortcut that is the output of the command :

```bash
commit 38a0c81fee06c009be2a714b6551be5e5a3ce5e7 Author: fredd**** fredd@*(mailto:fredd@**********)*** Date:   Thu Oct 22 16:38:36 2020 +0100

      dealing with it

commit 46b9d534a1484f0bb6ce71f72daf2304f25e1740 Merge: a11668f 8a93c07
Author: fredd*** [fredd@](mailto:fredd@**********)*** Date:   Thu Oct 22 16:18:09 2020 +0100

      changes in these

commit a11668f55720ab4c9526b587a0b5dae3c203c8ad Author: fredd*** [fredd@](mailto:fredd***********)***** Date:   Thu Oct 22 16:17:29 2020 +0100 

    fix something
```

### little messy here... not easy to understand , lets do something :

```bash
[alias]
c = !git add --all && git commit -m
s = !git status -s
l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn , %C(green)%cr'
```

**\--pretty=format:** -> flag to create a format pattern

**%h** -> short hash of the commit

**%d** -> branch and tag of commit

**%s** -> subject of commit (message)

**%cn** -> git user of commit

**%cr** -> Relative date of commit

**%C(blue)** -> Colors , colors everywhere , change text colors with this!

### Oh my God .. look at this bellow :

```bash
7a37d7e make it work - freddneos , 8 hours ago
6505576 change in these - freddneos , 8 hours ago
aa0e245 fix something - freddneos , 9 hours ago
```

Final format of our file (.gitconfig) : 

```bash
[user]
	email = fredd@*****
	name = freddneos
[core]
	editor = code
[alias]
	c = !git add --all && git commit -m
	s = !git status -s
	l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn , %C(green)%cr'
```

File Gist ->  [Gist]("https://gist.github.com/freddneos/a650daaccdf5f5a6c03d751f70792d3a.js")

That is it Dudes , With simple lines of code you have all the power to be more productive in git routines, that is something that we need to do every time and a lot of times in our day.

Go on and create others shorthands

Thanks for read this!!! Good Luck and God bless You!!!
