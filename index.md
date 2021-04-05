## Welcome to Green and Black

This repository concerns (a) working on a PC (b) with Ubuntu (Debian) Linux installed (c) feeling very unhappy with color-coded 
text in bash and vi (vim) and (d) changing it to all be green text on a black background. This 
personal bias was acquired in the mid 1980s.


All of this material is available on StackOverflow etcetera; but I wearied of re-looking-it-up all the time.


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


### vim:

`vi` and `vim` are the same thing: A text editor with arcane syntax inherited from an earlier editor called `ed`. 
To disable a profusion of colorized text in the editor: In escape mode type `:syntax off`. 


To disable a profusion of colorized text **permanently** create (or open the existing) file `~/.vimrc` and
append the text line `syntax off`.


### Which version of the operating system am I running? 

`hostnamectl`



