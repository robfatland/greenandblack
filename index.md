## Wait: How is this nice format built? 

I used a **gh-pages** as a separate branch from **main**. A jekyll template gives us nicer documentation.
The nice view is [here](https://robfatland.github.io/greenandblack/). But how???


- To start: Create some repository. This one is **greenandblack**
- Github --> repo --> Settings --> **pages** tab on the left. Choose a theme
- Switch to the `gh-pages` branch (from `main`: use the chooser
- Edit file `index.md`



Uh oh... months have gone by... 'How did I set this up? How do I change it?' 

- Find the branch chooser and switch to gh-pages
- Voila the `index.md` file appears 
- Edit! Commit! 
- The new version may be slow to appear... refresh!



## Just make it green and black


This repository concerns:


- working on a PC peering into another machine via an...
- ...installed Ubuntu (Debian) Linux bash shell
- ...where I am very unhappy with nauseating color-coded text 
- ...that assert whilst I am using both **bash** and **vi**
- ...with the addition of an "helpful" (stupid) prompt
- ...I wonder how much effort to get simple green on black


This personal bias was acquired by the author in the mid 1980s.


There is nothing tricky here; I just got tired of looking it up all the time.


### bash: 

(1) In the top window bar right click, select Properties, and set Color to green on black, increase font size, etcetera

We are not done because by default color support is enabled. To see this type `ls -al`.

(2) Comment out these lines in `.bashrc`

```
# enable color support of ls and also add handy aliases
#if [ -x /usr/bin/dircolors ]; then
#    test -r ~/.dircolors && eval "$(dircolors -b ~/.dircolors)" || eval "$(dircolors -b)"
#    alias ls='ls --color=auto'
#    #alias dir='dir --color=auto'
#    #alias vdir='vdir --color=auto'
#
#    alias grep='grep --color=auto'
#    alias fgrep='fgrep --color=auto'
#    alias egrep='egrep --color=auto'
#fi
```

Then re-run it: `source ~/.bashrc`


### stupid prompt


As long as we are making non-recommended changes to **bashrc**: To change that stupid 
over-complicated bash prompt:  Once again
open `~/.bashrc' in an editor, scroll down past all the `$PS1` stuff (this is a variable for the
default bash prompt) and put in something like 

```
PS1="my computer> "
```

and then save it and re-run **bashrc**. Now I know which bash shell is running on my local machine;
and I will use a different prompt for a cloud VM and so on. The prompt's job is just to remind 
me which computer it is running on. 


Because I use Anaconda: The current environment name gets prepended to my bash prompt so 
when I log in the prompt looks like `(base) my computer> `. This is ok by me because I switch
environments a lot. For example `conda activate fred_env` will change my prompt to 
`(fred_env) my computer> ` which is helpful to see at a glance. 

## ls:

To change the colors of the text produced by `ls` you can read an online resource like [**this one**](https://linuxhint.com/ls_colors_bash/).
I will give the bare-bones here, changing directory names to plain (not bold) green. 


* Append the current **ls** color scheme to the `.bashrc` file using `dircolors -b >> .bashrc`.
* Edit `.bashrc` and go to the end of the file where the output has created a big block of text:

```
LS_COLORS=`rs=0:di=01....etcetera etcetera etceters....;export LS_COLORS`
```

* These are key-value pairs. 
* The color green is '32' so find the entry for `di` (directory) and set it to `di=01;32`. 
* Save and execute `.bashrc`


## vim:

`vi` and `vim` are the same editor, specificially an ancient text editor 
with arcane syntax inherited from an even older editor called `ed`. 
To disable a profusion of colorized text in the editor: In escape mode type `:syntax off`. 


To disable a profusion of colorized text **permanently** create (or open the existing) file `~/.vimrc` and
append the text line `syntax off`.


## Which version of the operating system am I running? 

`cat /etc/os-release` or `lsb_release -a`



