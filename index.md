## Welcome to Green and Black

This repository concerns (a) working on a PC (b) having an Ubuntu installation (c) getting really uncomfortable with the color-coded 
text and (d) making it all green text on a black background: For both the bash terminal and the vim editor. This dates back to my
personal bias accrued in the mid 1980s. You can find all of this material on StackOverflow etcetera; I just finally got fed up with
having to re-look-it-up all the time; in part because I work with cloud VMs and IDEs where suddenly I find everything is color coded
again. 


### bash: 

(1) In the top window bar right click, select Properties, and set Color to green on black, increase font size, etcetera

We are not done because by default color support is enabled. To see this type `ls -al`.

(2) Comment out these lines in `.bashrc`

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
