# web-master-class

This master class will teach you how to become proficient as a web developer, with the necessary disciplines that you need to understand along the way, so that you become a master yourself. To achieve this particular goal, there will be no hand holding: you'll be given some essential pointers, but it is your job to seek the knowledge yourself.

## Contents

- [Introduction](#introduction)
- [Terminal](#terminal)
  - [How to interact with your terminal](#how-to-interact-with-your-terminal)
  - [Navigating directories](#navigating-directories)
    - [A small intermission about manual pages](#a-small-intermission-about-manual-pages)
  - [Playing around with files](#playing-around-with-files)
  - [Environment variables](#environment-variables)
    - [What is a variable anyway?](#what-is-a-variable-anyway)
  - [Chaining commands](#chaining-commands)
    - [Pipes](#pipes)
    - [And](#and)
    - [Or](#or)
    - [Combining everything](#combining-everything)
- [Text editor](#text-editor)
- [Version control system](#version-control-system)
- [Programming](#programming)
- [Web framework](#web-framework)
- [Dynamic pages](#dynamic-pages)
- [To be included]

## Introduction

Welcome to this master class. I'm glad that you are here. By the end of this journey, you should have a good grasp of what it means to be a software engineer, or at least a competent web developer. Ok, in the very least, I wish you to become a self-sufficient power user. There are no prerequisites and knowledge seekers of all levels are welcome to learn a thing or two from this material.

Important: this document makes no assumptions about what kind of computer system you are using. Since you're here, you're most likely using some [POSIX](https://posix.opengroup.org/)-compliant system, but it doesn't have to be. In any case, it's also your job to make sure the essential tools we're covering in this class do run properly in your own computer system. No hand holding, remember? So if you ever stumble upon something that doesn't work as expected, I'm pretty sure you can use [a decent search engine](https://www.ecosia.org/) and search for some instructions on how to install and make such thing work on your own system of choice. You did choose your current system, didn't you?

## Terminal

In the beginning, there was just the terminal. Actually, in the real beginning not even that, but we live in privileged times and we can fast forward to taking it for granted. Fancy graphical desktop environments came much later, but they never replaced the terminal. And you're about to learn why. Picture this: the desktop environment is to the terminal pretty much what early sketching inside caves is to modern written language. If you want to convey advanced instructions, pointing at icons becomes very limiting, very quickly.

The day of any decent software engineer usually begins and ends in the terminal, so you might as well get used to it sooner than later. Go ahead, open your "Terminal" application, unless you are already in it. The terminal is your biggest friend now, keep it around the corner at all times. As soon as you open it, you might see some text already there and a cursor. That's provided by a program that handles your interaction with the terminal and is usually known as your "shell". Let's cover some basics of how to actually use it.

### How to interact with your terminal

Here's the deal: from now on, whenever you see a block like this:

```shell
ls
```

You will just type it in the terminal, exactly how it's written, line by line, hitting "Enter" at the end of each line. You might feel tempted to just copy and paste everything but I urge you not to do that, because typing is important for building muscle memory. And you want that because these commands will become your trusty companions for as long as you keep using computers. Deal? Then look at what that `ls` command you just typed produced. You should see a list of the contents in the working directory (also known as current folder). And what would such "working directory" be, you might ask? Luckily, there's another command to answer that:

```shell
pwd
```

You might see something that ends with your username. Not sure? Well, you guessed, there's also another command for that too:

```shell
whoami
```

Let's also try this one:

```shell
echo 'Hello!'
```

I'll let you guess what this one does. You see? Typing in the terminal is quite analog to having a chat with your computer. Except instead of using some wild natural language, you're using a formal language, which is unambiguous.

One more important command before we move forward:

```shell
exit
```

As you can imagine, that one ends your current shell session. It's always a good idea to formally end your terminal session like this, because it gives your shell a chance to save any pending information such as your history, etc. Talking about that, please open your terminal again and try this:

```shell
history
```

You should see a list of the latest commands you've typed into your terminal. That's your history for you.

### Navigating directories

Now that you know how to list the contents of the working directory, you might want to change to another directory. Can you tell which among those contents are also directories or just some plain files? Let's try this:

```shell
ls -l
```

You should see a list of contents, but with some extra information, split into columns. The first column is that we call "file mode". Some of them might have a "d" at the beginning of their file mode attributes, which means those are also directories (folders).

By the way, you might have just noticed that `ls -l` is just `ls` again, with an additional flag, `-l` in this case. You might wonder how many of these `ls` might have, and I'm glad you do. How can you learn more about them? So here's another very important command for you:

#### A small intermission about manual pages

```shell
man ls
```

Nice, you've just found the manual for `ls`. You can usually exit that by typing `q` (for "quit"). Go on, try checking the manual for the previous commands we used before:

```shell
man echo
man pwd
man whoami
```

And in case you are wondering, you probably guessed it right, you can read the manual for `man` itself as well:

```shell
man man
```

---

Coming back to what we were doing, now you can try changing your working directory to one of those directories that were listed before (the ones with a "d" file mode). In case you don't have any directories, or for the sake of this exercise, we can also create our own directory, for example:

```shell
mkdir Directory
```

Now you can do:

```shell
cd Directory
```

Of course, please replace `Directory` above which whatever other directory you have or prefer. Now, when you type in these commands:

```shell
pwd
ls
```

You'll notice the output should be different. First, `pwd` will return the now current directory. Also `ls` will return the contents of this new current directory. You might have noticed a couple of entries are always present when you `ls`, namely "." and "..". These are special directories, the first one being a reference to the very directory containing it and the second one being a reference to its parent directory. This can be useful, for example if you want to go back to the parent directory":

```shell
cd ..
pwd
```

Please not that now you're back to the previous directory, before you `cd`-ed into the child one. Also, you can always come back to your "home" directory by issuing `cd` without any arguments:

```shell
cd
```

At the time of this writing, I couldn't find a manual page for the `cd` command by issuing `man cd`. I think this speaks for itself about how essential a command `cd` is, you just _have_ to know it. In case you have wondered, its name means "change directory", by the way.

### Playing around with files

Now that we had some fun with directories and know how to navigate between then with confidence, let's play with some files. Start by creating a new file:

```shell
touch just_a_sample_file.txt
```

If you list the contents of the current directory, you should see the newly created file there:

```shell
ls
```

Now let's add something to this new file, for example:

```shell
echo 'Hello world!' >> just_a_sample_file.txt
```

That `>>` is called the "append redirection operator" and will basically whatever comes out of `echo` to the target file, in append more. Let's take a look at the contents of that file now:

```shell
cat just_a_sample_file.txt
```

You might have noticed it contains exactly what you just put in it. Let's repeat that other command a few more times. You might want to give the up cursor arrow in your keyboard a try, as it will make it easier repeating your previous commands:

```shell
echo 'Hello world!' >> just_a_sample_file.txt
```

Now list the file's contents again:

```shell
cat just_a_sample_file.txt
```

See what happened there? That's what it means to "append" something to a file, you're not overriding it, just adding more stuff every time. Now there's another equally important operator to be learned:

```shell
echo 'Hello world!' > just_a_sample_file.txt
cat just_a_sample_file.txt
```

If you only see "Hello world!" once now, that's what you expected, because that `>` is just a "redirection operator" in overwrite mode, it will get rid of whatever was in that file before writing the new stuff. As you might have guessed, this can have destructive effects, so you might want to use it with care, especially if that target file contained a very long novel you had just typed.

Now let's see how we can rename that file:

```shell
mv just_a_sample_file.txt another_sample_file.txt
ls
```

You might have noticed that file now has a different name. And how can we move it around?

```shell
mv another_sample_file.txt Directory
ls
ls Directory
```

As you might have guessed, the file is now in that new Directory we created before. Let's move it back:

```shell
mv Directory/another_sample_file.txt .
ls Directory
ls
```

That was a lot of fun. Always pay attention when moving files around, as you don't want to move them somewhere you can't remember later. And as you probably guessed, you can also move directories with `mv` too.

A good practice when dealing with files and directories in general is not leaving some garbage behind, so let's get rid of that sample file we've just created:

```shell
rm another_sample_file.txt
ls
```

You'll notice "another_sample_file.txt" is no longer part of the current directory's contents. Bye bye! We can also get rid of that sample directory we created just to play around:

```shell
rmdir Directory
```

Just please, don't get trigger happy now and don't start deleting every file around, as you might lose some important data and dearly regret it later.

### Environment variables

Another important concept while learning to use the terminal is understanding environment variables. They can directly or indirectly affect the outcome of your commands and programs, so it's best to know how they work.

#### What is a variable, anyway?

So before we dig into environment variables, let's learn what is a variable first. I was planning to introduce this in the [Programming](#programming) chapter below, but let's break the ice right now. A variable is simply a labeled space in the computer memory that stores some information. Let's create a variable to see that in action:

```shell
MY_FIRST_VARIABLE='Wow, this is so cool!'
echo $MY_FIRST_VARIABLE
```

See? You've just created a variable, stored some text inside it, then displayed its contents afterwards. That's a local variable, and it only lives within the scope of your current shell. If you `exit` your shell and open a new terminal, this variable won't be there anymore. Also if you open another terminal, it won't be there, too. You can try it out and see for yourself.

---

Coming back to environment variables, here are a couple important ones:

```shell
echo $PATH
echo $SHELL
```

The first one is the "path" for your shell. So that when you type a command, e.g. `cat` (which is a program, by the way), your shell needs to know where to look for it (since it's not in your current directory). For that purpose, it resorts to the path, and it might find it somewhere along those directories you can see listed in the contents of the `PATH` variable.

The second one is your shell interpreter itself. Some common ones are `bash`, `sh`, and `zsh`. There are others of course, but an extensive list of all known shell programs is beyond the scope of this chapter. It can be useful to know what kind of shell you are using though, as they might have different features which you might be interested into.

Environment variables are special because they are exported to child processes (programs). Let's try this out:

```shell
MY_VARIABLE='Not for export!'
sh
echo $MY_VARIABLE
exit
```

You'll notice that when you `echo` there will be no output. Why? Because the variable you created in your parent shell was never exported to the child shell (created when you issue `sh`). So how can we overcome that? Let's see in the next sequence of commands:

```shell
export MY_VARIABLE='Too good for domestic!'
sh
echo $MY_VARIABLE
exit
```

Thanks to the `export` keyword, the variable was now successfully accessed from the child shell. In effect, the exported one is now an environment variable.

So if I tell you that your current shell is also a child of some other process, you might wonder how many exported variables are part of its environment. Fortunately there's a better way than trying to guess their names:

```shell
env
```

You might be surprised with the amount of environment variables you will see in a modern system. And by the way, your exported `MY_VARIABLE` should be among them, too.

This is the explicit way of declaring environment variables. There's also an implicit way, which is often used but seldom talked about:

```shell
MY_VARIABLE='Just for you!' sh
echo $MY_VARIABLE
exit
```

As you can see, the variable was accessible from within the child shell, even though you didn't explicitly export it from the parent shell, but since you declared it just before issuing the command, it became part of its environment. That's called an implicit export.

Why are environment variables important, anyway? They can be used for many purposes, commonly applied to environment configuration. Many behaviors and settings can be adjusted simply by setting some different values to environment variables.

### Chaining commands

Picture this: you're in charge of managing the flow in a laundry. The flow goes from the washer, through the dryer and folding to the closet. There's a person taking care of each of these activities, but it is your job to carry the items between each of them once every step is done. It's a lot of work, isn't it? Now imagine you had a conveyor belt connecting all of these stations. As soon as the work is done in the first station, it is automatically carried over to the next, and so forth. Your job would become much easier, wouldn't it?

Luckily in the terminal you can chain commands, turning the output of one command into the input of the next one. Let's have a look at the operators that allow us to do that.

#### Pipes

Suppose you'd like to know how many processes you are running right now under your own user account. How many, do you guess? You main count your browser, some email client, a couple terminals... maybe you're also running a music player as you read this document. Do you think that's it? Let's find out, shall we? First, let's list them:

```shell
ps aux
```

You might be surprised with the size of that list, and also how many of those entries have your username on them. I bet you couldn't even see the whole list because it scrolled up. Let me help you with that:

```shell
ps aux | more
```

Now you can see the first complete page, before moving forward to the next page. One thing you might have noticed here is that the first line contains headers, with "USER" being the first column. Now you can hit "Enter" to proceed line by line or "space" to proceed page by page. If you ever get bored, you can also hit `q` to quit. That's the convenience the `more` program is bringing to you. How does that work? Well, the `ps` command has long completed its task, which was listing the processes, and then it handed that output over to `more`, which took over and is paginating it for you. Neat, isn't it? I bet you will also like this other program:

```shell
ps aux | less
```

That's yet another pager, and these days many people prefer `less` over `more`. Maybe it's because "less is more". One of its advantages, being that you can also navigate backwards (`more` only goes forward).

It will be still quite tedious counting all of those lines that contain your username one by one. Maybe if at least you'd see a list with just the entries you care about?

```shell
ps aux | grep $(whoami) | less
```

That's better, isn't it? Now you should see only the entries with your username on them. By the way, you might have noticed a few things there. The most obvious is that now you probably realized you can pipe the output of one command over to the next one indefinitely. Another thing is the `grep` command over there, quite useful that one. Make sure you visit its `man` page very soon. And last but not least, there's the `$()` operator wrapping the `whoami` command. What does that do? That's a command substitution. It executes whatever is inside first, `whoami` in this case, returning its value in place, so that it can be used as the argument for `grep`. Cool, isn't it?

Alright, this is making it easier and easier for you to count how many processes you are running at the moment. But computers are big calculators, aren't they? I'm sure they can "count" things for you. Let's try this:

```shell
ps aux | grep $(whoami) | wc -l
```

With that, the last program receiving the output from the previous one is `wc`, which can count words for you, in this case full lines, since we're using the `-l` flag. I hope that by now I don't have to suggest that you have a look at its `man` page when you get a chance. And I think now you have a good grasp at how many processes you are running yourself.

#### And

Now, suppose you want to chain tasks, but only if the previous task is successful. Let's try this:

```shell
cat some_file_that_does_not_exist.txt && echo 'I found the file!'
```

You should notice two things: first is some error message from `cat` stating that it did not find such file, and second, your `echo` command never printed the "I found the file!" message, because it was never executed, thanks to the `&&` (and) operator connecting them. Let's give it another try:

```shell
touch some_file_that_now_exists.txt
cat some_file_that_now_exists.txt && echo 'Now I actually found the file!'
```

That looks nicer, doesn't it? First, you shouldn't have seen any error message from `cat` this time, and now your `echo` command should have executed, displaying the friendly message you just typed there. By the way, you might want to get rid of that sample file with `rm`, since you already know how to use it.

#### Or

What if you want the computer to try doing something, or something else, in case the first thing fails? That's what the `||` (or) operator is for. Let's see that in practice:

```shell
cat some_file_that_does_not_exist.txt || echo 'I could not find such file!'
```

That `cat` should fail, displaying its own error message, but your `echo` will also execute. Let's try something different now:

```shell
echo 'This will succeed!' || echo 'The previous command failed!'
```

As you can see, the first `echo` did indeed succeed, while the second `echo` was never executed, because of precisely that.

#### Combining everything

Now that we know these operators, we can combine them all together for more complex tasks. Let's see if you can make your computer find the needle in the haystack:

```shell
touch haystack.txt
(cat haystack.txt | grep 'needle') && echo 'I found it!' || echo 'I could not find it!'
echo 'needle' >> haystack.txt
(cat haystack.txt | grep 'needle') && echo 'I found it!' || echo 'I could not find it!'
```

That was fun, wasn't it? Maybe you noticed the parentheses there, they were added to tell the computer that `cat haystack.txt | grep 'needle'` is the expression you want to be evaluated by the following logical operators. You can also get rid of that new `haystack.txt` file with `rm` now.

## Text editor

Now that we know how to navigate directories and manage some files, let's have a look at how we can edit those files. There must be a more convenient way to write text to files than `echo` into files with an append redirection operator, right?

While there are many popular Text editors available, there's one in particular that is at the same time quite powerful and pretty much ubiquitous. That's VI. If you ever log into a terminal, be it an IBM AS/400 from the 80s, or a modern GNU/Linux operating system you've just freshly installed, I'm quite sure VI will be there. And that's great.

So let's get started with some VI basics:

```shell
vi some_new_file.txt
```

That command should open VI, editing a brand new file. What you see next is VI's user interface. VI is sophisticated and has different modes of operation. As soon as you start VI, it will be in "command" mode. That means whatever you type is supposed to be a command. We'll dive into that soon enough.

What we want to do now is enter another mode, called "input" mode. For that, we'll type `i` (for input). Once you do that, you can type whatever you want, e.g. `Hello!`. If you make any mistakes while typing, you can hit Backspace as much as you need and try it again.

Once you're happy with what you've typed, hit ESC (also known as the Escape key, usually in the top left corner of your keyboard) to go back to "command" mode. Back in "command" mode, type `:x` and hit Enter. You should have now left VI's interface and be back in your usual terminal prompt.

Now, if you do:

```shell
ls
cat some_new_file.txt
```

You'll see the new file is there when you list the directory's contents and also the file's own contents when you display it with `cat`. That was easy, wasn't it? But that's not all there is to it when it comes to VI. It has many other features that we'll explore together.

Open that file again. If you hit the up arrow in your keyboard a few times, you'll come back to the `vi some_new_file.txt` command. Then you just hit Enter to run it again. That's the convenience of keeping a `history`, as seen before. Make sure you type some lines of text now, anything goes. Make sure you have at least some five lines of text there. They don't have to be long. Also make sure you have the word "tofu" somewhere. You know how to do it, right? Enter the input mode with `i` and start typing. Hit Enter whenever you want to add a new line.

Now that you have typed some 5+ lines of text with the word "tofu" somewhere, let's learn a few more Vi commands. Hit ESC on your keyboard to go back to command mode, if you haven't already.

Suppose you want to go to a specific line of your text. You can do that with the command:

```shell
:5
```

That should take you to the beginning of line 5. Should you want to go to another line, you'd replace that `5` with some other number. If you go overboard, Vi will also tell you that such line doesn't exist. Now that you know that, go back to the first line:

```shell
:1
```

What if you don't like that line? You can delete it with the `dd` command. That line should be now gone. It's a little sad, isn't it? Let's bring it back, with the undo command:

```shell
:u
```

There you go, the line you just deleted should have been brought back. But then you look at it again and you really don't like it. Actually, you don't like any of those 5 first lines of text. Luckily, in Vi you can precede most commands with a number that will tell Vi how many times you want it to repeat that command. So let's get rid of those first 5 lines:

```shell
5dd
```

Five full lines of text should be now gone. But you actually really liked them, so let's bring them back one more time with the undo command you just learned. And now we'll duplicate those lines, with this command:

```shell
P
```

Wow, what happened there? Well, when you first deleted those lines, they were put in a buffer, think of `d` as a line cutter. So when you use the `P` (paste on top) command, whatever was in that buffer gets pasted into the text. Neat! Now what if you'd just like to copy and paste, without cutting first? We can also do that. Try this:

```shell
3yy
p
```

That tells Vi to copy 3 lines with the `y` (yank) command, then paste on bottom with the `p` command. As you'll probably realize, pasting on bottom or top can be more or less convenient depending on what you are trying to do.

What about that magic word we typed before, do you know where it is? Or even if you have it in multiple places now? Let's find out, with the help of the search command:

```shell
/tofu
```

I hope you found at least one, otherwise Vi will tell you that it cannot find it. But everything went well, you should probably have at least two of them now. How can you find the other one? With the "next" command that is:

```shell
n
```

You can keep hitting `n` until you find the one you're looking for, and Vi will loop back to the first one when you find the last one and hit `n` again. You can also move backwards, with the `N` command.

(to be continued)

## Version control system

## Programming

## Web framework

## Dynamic pages

## To be included

This chapter is about everything that should be included in the above pages. It can be used to improve future versions of this master class, but it can also be useful to you, reading this very version right now, hinting about other topics you should learn. Remember, you yourself own your own journey towards knowledge.

- Terminal
  - Wildcards (*, ?) and other expressions that can be used with file names
  - Iterators (for loops)
