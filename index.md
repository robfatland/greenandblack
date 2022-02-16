## Nice format! What's your secret? 


First: This is about retro-customizing your UNIX working environment, not 'nice formatting'... but ok:


I used the **gh-pages** service; which involves using a separate branch from the default **main**. 
**gh-pages** uses a jekyll template for nicer-looking documentation.
This is published [here](https://robfatland.github.io/greenandblack/) and here are the steps:


- Create some repository, like this **greenandblack** one, on GitHub
- Menus: Github --> repo --> Settings --> **pages** tab on the left, then choose a *theme*
- Switch to the `gh-pages` branch (from `main`: use the chooser)
- Edit the file `index.md`. That becomes what you see... like these words


Uh oh... several months have gone by... I forgot everything! How did I set this up? More important, how do I edit it?


- Find the branch chooser for the repo and use it to switch to the gh-pages branch
- There is the `index.md` file: Edit it! Commit! Go check the website: https://**organization**.github.io/**repo**
- In this case that is https://robfatland.github.org/greenandblack
    - An edited version may be slow to appear... refresh!



## Just make it green and black


Ok back to the purpose here. This repository concerns:


- working on a PC peering into another machine via an...
- ...installed Ubuntu (Debian) Linux bash shell
- ...where the author is very unhappy about nauseating colorized text 
- ...that appears both in the **bash** shell and the **vi** editor
- ...including a "helpful" (stupid) prompt
- ...and all I want is simple green on black


This personal bias was acquired by the author in the mid 1980s. Because Curtis Ling is cool, even if he is late for rehearsal.


There is nothing tricky here; I just got tired of looking this up all the time.


### fixing **bash** 


Again this is an Ubuntu bash shell installed on a Windows PC. Ubuntu is Linux, and that means UNIX. 


(1) Run the Ubuntu bash shell and from the top window bar: Right click, select Properties, and set Color to green on black
(2) Increase font size and adjust whatever else you like


We are not done: Color support is still enabled. For example, type `ls -al`.


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
I give the bare-bones here for making directory names green. 


* Append the current **ls** color scheme to the `.bashrc` file using `dircolors -b >> .bashrc`.
* Edit `.bashrc` and go to the end of the file where the output has created a several lines of dense text:

```
LS_COLORS=`rs=0:di=01;34....etcetera etcetera etceters....;export LS_COLORS`
```

* These are key-value pairs. 
* The color green is '32' so find the entry for `di` (directory) and set it to `di=01;32`. 
* Save and run the file `.bashrc`


## vim:

`vi` and `vim` are the same editor, specificially an ancient text editor 
with arcane syntax inherited from an even older editor called `ed`. 
To disable a profusion of colorized text in the editor: In escape mode type `:syntax off`. 


To disable a profusion of colorized text **permanently** create (or open the existing) file `~/.vimrc` and
append the text line `syntax off`.


## Which version of the operating system am I running? 

`cat /etc/os-release` or `lsb_release -a`



