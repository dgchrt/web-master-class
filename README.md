# web-master-class
Web Master Class

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
- [Text Editor](#text-editor)
- [Version Control System](#version-control-system)
- [Programming](#programming)
- [Web Framework](#web-framework)
- [Dynamic Pages](#dynamic-pages)

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
export MY_VARIABLE='Too good for domestic!'
sh
echo $MY_VARIABLE
exit
```

You might have noticed that the first local variable wasn't accessible in the child shell program, while the second, thanks to the `export` keyword, was. In effect, the exported one is now an environment variable.

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

(to be continued)

### Chaining commands

## Text Editor

## Version Control System

## Programming

## Web Framework

## Dynamic Pages
