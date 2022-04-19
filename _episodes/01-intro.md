---
title: "Introducing the Shell"
teaching: 5
exercises: 0
questions:
- "What is a command shell and why would I use one?"
objectives:
- "Explain how the shell relates to the keyboard, the screen, the operating system, and users' programs."
- "Explain when and why command-line interfaces should be used instead of graphical interfaces."
keypoints:
- "A shell is a program whose primary purpose is to read commands and run other programs."
-  "This lesson uses Bash, the default shell in many implementations of Unix."
-  "Programs can be run in Bash by entering commands at the command-line prompt."
- "The shell's main advantages are its high action-to-keystroke ratio, its support for
automating repetitive tasks, and its capacity to access networked machines."
- "The shell's main disadvantages are its primarily textual nature and how
cryptic its commands and operation can be."
---

### Background

Humans and computers commonly interact in many different ways, such as through a keyboard and mouse,
touch screen interfaces, or using speech recognition systems.
The most widely used way to interact with personal computers is called a
**graphical user interface** (GUI).
With a GUI, we give instructions by clicking a mouse and using menu-driven interactions.

While the visual aid of a GUI makes it intuitive to learn,
this way of delivering instructions to a computer scales very poorly. There may also be times
when you have to
interact with certain programs or environments without a GUI.

This is where the Unix shell comes in.

The Unix shell is both a **command-line interface** (CLI) and a scripting language,
allowing repetitive tasks to be done automatically and fast.
With the proper commands, the shell can repeat tasks with or without some modification
as many times as we want.

Personal example:
I was excited to teach this workshop not because I am someone that lives in the command line
or has even been
using it for many years but rather because there have been a few instances in my day-to-day
work where the power
of this tool has made a huge difference. I manage a collection of websites and
databases as part of the services
offered by the Digital Archaeology Lab and so have regular backups that need to be conducted.
With the command
line and a few scripts, I can backup the 30+ sites (all of the files and underlying
databases) in around 15
minutes. If I were to try to do this manually using the GUI available to me, it takes
somewhere between half a
day to a full day of work...depending on how often I am distracted from sheer boredom waiting
for progress bars to
complete.

So even if you are working in environments that offer a GUI, being comfortable enough with
the shell to input
commands and follow tutorials or guides online that assume you will be using the command line
is extremely helpful.

### The Shell

The shell is a program where users can type commands.
With the shell, it's possible to run complicated programs like climate modeling software
or simple commands that create an empty directory with only one line of code.
The most popular Unix shell is Bash (the Bourne Again SHell ---
so-called because it's derived from a shell written by Stephen Bourne).
Bash is the default shell on most modern implementations of Unix and in most packages that
provide Unix-like tools for Windows.

Learning how to use the shell may not be intuitive at first - it certainly wasn't for me.
With a GUI you're given
choices that you can select from, with the shell you have to know what to type, kind of like
learning a new vocabulary in a language. However, unlike a spoken language, a small number of
"words" (i.e. commands)
gets you a long way, and we'll cover those essentials today.

The grammar of a shell allows you to combine existing tools into powerful
pipelines and handle large volumes of data automatically. Sequences of
commands can be written into a _script_, improving the reproducibility of
workflows.

In addition, the command line is often the easiest way to interact with remote machines like
a server and supercomputers.
Familiarity with the shell is near essential to run a variety of specialized tools and
resources including high-performance computing systems.
As clusters and cloud computing systems become more popular for scientific data crunching,
being able to interact with the shell is becoming a necessary skill.
We can build on the command-line skills covered here
to tackle a wide range of scientific questions and computational challenges.

Okay, let's get started!

When the shell is first opened, you are presented with a **prompt**,
indicating that the shell is waiting for input.

```
$
```
{: .language-bash}

The shell typically uses `$ ` as the prompt, but may use a different symbol.
In the examples for this lesson, we'll show the prompt as `$ `.
Most importantly:
when typing commands, either from these lessons or from other sources,
_do not type the prompt_, only the commands that follow it.
Also note that after you type a command, you have to press the <kbd>Enter</kbd> key to execute it.

The prompt is followed by a **text cursor**, a character that indicates the position where your
typing will appear.
The cursor is usually a flashing or solid block, but it can also be an underscore or a pipe.
You may have seen it in a text editor program, for example.

So let's try our first command, `ls` which is short for listing.
This command will list the contents of the current directory:

```
$ ls
```
{: .language-bash}

```
Desktop     Downloads   Movies      Pictures
Documents   Library     Music       Public
```
{: .output}

> ## Command not found
>
> If the shell can't find a program whose name is the command you typed, it
> will print an error message such as:
>
> ```
> $ ks
> ```
> {: .language-bash}
>
> ```
> ks: command not found
> ```
> {: .output}
>
> This might happen if the command was mis-typed or if the program corresponding to that command
> is not installed.
> {: .callout}

## Nelle's Pipeline: A Typical Problem

We're going to use an example project to practice the commands we're learning today. Our
example revolves around a marine biologist named Nelle Nemo, who has just returned from a
six-month survey of the
[North Pacific Gyre](http://en.wikipedia.org/wiki/North_Pacific_Gyre),
where she has been sampling gelatinous marine life in the
[Great Pacific Garbage Patch](http://en.wikipedia.org/wiki/Great_Pacific_Garbage_Patch).
She has 1520 samples that she's run through an assay machine to measure the relative abundance
of 300 proteins.
She needs to run these 1520 files through an imaginary program called `goostats.sh` she
inherited.
On top of this huge task, she has to write up results by the end of the month so her paper
can appear in a special issue of _Aquatic Goo Letters_.

The bad news is that if she has to run `goostats.sh` by hand using a GUI,
she'll have to select and open a file 1520 times.
If `goostats.sh` takes 30 seconds to run each file, the whole process will take more than 12
hours of Nelle's attention.
With the shell, Nelle can instead assign her computer this mundane task while she focuses
her attention on writing her paper.

The next few lessons will explore the ways Nelle can achieve this.
More specifically,
they explain how she can use a command shell to run the `goostats.sh` program,
using loops to automate the repetitive steps of entering file names,
so that her computer can work while she writes her paper.

As a bonus,
once she has put a processing pipeline together,
she will be able to use it again whenever she collects more data.

In order to achieve her task, Nelle needs to know how to:

- navigate to a file/directory
- create a file/directory
- check the length of a file
- chain commands together
- retrieve a set of files
- iterate over files
- run a shell script containing her pipeline

{% include links.md %}
