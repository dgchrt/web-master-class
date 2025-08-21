# web-master-class
Web Master Class

This master class will teach you how to become proficient as a web developer, with the necessary disciplines that you need to understand along the way, so that you become a master yourself. To achieve this particular goal, there will be no hand holding: you'll be given some essential pointers, but it is your job to seek the knowledge yourself.

## Contents
- Introduction
- Terminal
- Text Editor
- Version Control System
- Programming
- Web Framework
- Dynamic Pages

## Introduction
Welcome to this master class. I'm glad that you are here. By the end of this journey, you should have a good grasp of what it means to be a software engineer, or at least a competent web developer. Ok, in the very least, I wish you to become a self-sufficient power user. There are no prerequisites and knowledge seekers of all levels are welcome to learn a thing or two from this material.

Important: this document makes no assumptions about what kind of computer system you are using. Since you're here, you're most likely using some [POSIX](https://posix.opengroup.org/)-compliant system, but it doesn't have to be. In any case, it's also your job to make sure the essential tools we're covering in this class do run properly in your own computer system. No hand holding, remember? So if you ever stumble upon something that doesn't work as expected, I'm pretty sure you can use [a decent search engine](https://www.ecosia.org/) and search for some instructions on how to install and make such thing work on your own system of choice. You did choose your current system, didn't you?

## Terminal
In the beginning, there was just the terminal. Actually, in the real beginning not even that, but we live in privileged times and we can fast forward to taking it for granted. Fancy graphical desktop environments came much later, but they never replaced the terminal. And you're about to learn why. Picture this: the desktop environment is to the terminal pretty much what early sketching inside caves is to modern written language. If you want to convey advanced instructions, pointing at icons becomes very limiting, very quickly.

The day of any decent software engineer usually begins and ends in the terminal, so you might as well get used to it sooner than later. Go ahead, open your "Terminal" application, unless you are already in it. The terminal is your biggest friend now, keep it around the corner at all times. Let's cover some basics of how to actually use it.

### How to interact with your terminal
Here's the deal: from now on, whenever you see a block like this:

```shell
ls
```

You will just type it in the terminal, exactly how it's written, line by line, hitting "Enter" at the end of each line. Deal? Then look at what that `ls` command you just typed produced. You should see a list of the contents in the working directory (also known as current folder). And what would such "working directory" be, you might ask? Luckily, there's another command to answer that:

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

Coming back to what we were doing, now you can try changing your working directory to one of those directories that were listed before (the ones with a "d" file mode), for example, supposing one of the directories you see there is called "Downloads", you can do:

```shell
cd Downloads
```

Of course, please replace `Downloads` above which whatever other directory you have or prefer. Now, when you type in these commands:

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

A good practice when dealing with files in general is not leaving some garbage behind, so let's get rid of that sample file we've just created:

```shell
rm just_a_sample_file.txt
ls
```

You'll notice "just_a_sample_file.txt" is no longer part of the current directory's contents. Bye bye! But please, don't get trigger happy now and don't start deleting every file around, as you might lose some important data and dearly regret it later.

(to be continued)

## Text Editor

## Version Control System

## Programming

## Web Framework

## Dynamic Pages
