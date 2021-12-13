## Wait: What? How is this nice format built? 

I used a separate branch called gh-pages. This uses a jekyll template to create nicer looking documentation.
This seems to reside at `https://robfatland.github.io/greenandblack/`. Ok how did I get here???


- To start I create some sort of repository. This one is called ***greenandblack***.
- Within github I go to Settings and find the pages tab on the left. I choose a theme.
- I switch to the `gh-pages` branch (chooser at upper left) and edit `index.md`.
- Months have gone by and I'm wondering 'How did I originally do this???' 
    - Wait! There is that branch chooser in the upper left part of the main view screen. 
    - I change the branch to `github pages`; and voila this `index.md` file appears... 
    - So I edit and commit and so on. Sometimes it takes a few minutes for changes to register.



## Just make it green and black


This repository concerns (please apply AND):


- working on a PC 
- with an installed Ubuntu (Debian) Linux bash shell
- unhappy with the color-coded text 
- while using **bash** and **vi** (**vim**)
- plus the prompt is "helpful" (stupid)
- wondering how much effort it would be to go to green text on a black background


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



## vim:

`vi` and `vim` are the same editor, specificially an ancient text editor 
with arcane syntax inherited from an even older editor called `ed`. 
To disable a profusion of colorized text in the editor: In escape mode type `:syntax off`. 


To disable a profusion of colorized text **permanently** create (or open the existing) file `~/.vimrc` and
append the text line `syntax off`.


## Which version of the operating system am I running? 

`cat /etc/os-release` or `lsb_release -a`



