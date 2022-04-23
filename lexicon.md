# Lexicon

- [green and black: from the top, nice format](https://robfatland.github.io/greenandblack)
- [green and black: from the top, github](https://github.com/robfatland/greenandblack/blob/gh-pages/index.md)
- [green and black: this lexicon, nice format](https://robfatland.github.io/greenandblack/lexicon)
- [green and black: this lexicon, github](https://github.com/robfatland/greenandblack/blob/gh-pages/lexicon.md)


Here are all the answers to all the important questions in the circa-2022 data science ecosystem. 
Well, some of them anyway.


## Weasel??? Anaconda???  What, are we in some sorta zoo????


This is an unapologetic sequence of lexicon explanations, an infinite sequence of paragraphs. 


### What is Anaconda?


Anaconda is a **Python distribution** that features a metric ton of pre-installed data science libraries. 
Therefore we can say Anaconda is a **data science platform** that happens to use Python. 
But when Anaconda installs in a Linux operating system it also installs therein this special command `conda`.
The `conda` command is a package manager; so if I need more libraries I can try and install them using
`conda`. This installing business sounds like `pip` and even `apt-get`; so what is the distinction
between the three? 


### What is **`conda-forge`**?


### What is Miniconda? 


### What is WSL?

This is a bit of jargon that rests squarely on another bit of jargon. Once we have *that second jargon*
defined it is very easy to define WSL. So let us ask **'In computers, what is a *compatibility layer*?'**
A compatibility layer is an interface that allows binaries from a foreign system to run on a host 
system. 

So let's say the host system is Windows and the compatibility layer is Windows Subsystem for Linux, 
abbreviated WSL. And now version 2 is out; so technically WSL-2. WSL is built into the Windows operating
system on a PC; so it may need to be enabled in order to run Linux on that PC. 

Running a Windows Command Prompt as Administrator one can issue a `wsl` command that starts a bash shell
in the Command window. This sequence indicates 'going there and coming back again'.

```
C:\Windows\system32> wsl

(base) username> pwd

/mnt/c/WINDOWS/system32

(base) username> cd ~
(base) username> pwd

/home/username

(base) username> exit

C:\WINDOWS\system32>
```

### What is VSCode?


### What is **`bash`**?


### What is **`Linux`**?


### What is **`vi`** or **`vim`**?

[**`vi`** is a visual text editor](https://en.wikipedia.org/wiki/Vi)
created by Bill Joy back in the mid-1970s. **`vim`** is an improved 
and very compatible version. The main point of `vi` from my perspective
is: Sharp learning cost and then it becomes second nature; and this
is primarily due to the intrinsic <escape> mode which gives access
to a command line at the bottom of the screen.
  

In recent years `vi/vim` has accumulated features like color-coded
text which is one of the motivations for this repository. Apparently
when Heads Up Displays were introduced in the military the pilots 
would often switch them off because it they just amounted to visual clutter.



### What is **`Jupyter`**?


### What is **`git`**?


### What is GitHub?


### What is Binder?


### What is an environment?


### What is **`environment.yml`**?


### What is **`requirements.txt`**?


I can "install" something called WSL... or maybe it is combined with "turning on Linux" inside Windows. But I can also install Ubuntu bash. Which opens a bash terminal in my home directory... where miniconda is not installed. So I install miniconda and now I can create and activate environments. And I can start a Jupyter notebook server. But the other day my Ubuntu <start> icon stopped working. So I forced Ubuntu to start using the Windows start utility. So it started. So I said "ls" and everything was gone. So all my hard work evaporated (except that it was mostly synched with GitHub so Hah Hah Hah on the gods of data loss). So 
  
  
  ### What is a web framework?
  
  
  ### What is flask?
