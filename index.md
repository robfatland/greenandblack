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


# The Rest Of This Doc...


...concerns some common (cloud-related) tasks. I needed a place to keep these notes so I'm parking them 
here in a repository that I'm sure will stay around for some time. So DON'T DO THIS STUFF HERE unless
you are sure it is the right thing to do. 


## How do I get miniconda going? 


You know how there is that science fiction trope where yourself from the future
shows up to give you a warning before you do something stupid? Well this is me from the 
future. Again: Don't follow these instructions: I have not checked them recently. Unless you are sure 
you want to. 


```
wget https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
bash Miniconda3-latest-Linux-x86_64.sh
```

As this runs: Respond to the prompts with care; and continue with:

```
rm Miniconda3-latest-Linux-x86_64.sh
source ~/.bashrc
conda install ipython
conda install jupyter
conda create -n lectroid python=3.6
conda activate lectroid
(jupyter notebook --no-browser --port=8889) &
```

## What is the point of conda environments? 


The `create/activate` commands get us in the habit of treating a Python environment as a sub-framework of 
the generic general environment. Need: steps to ensure this environment appears in
the notebook server interface. 


## How to Tunnel

I want to run jupyter on a secure VM inside the AWS cloud on a private subnet. Let's call it **worker**.
I have an intermediary bastion server called **bastion**. I'm going to connect from my local machine to
**bastion** to **worker** so that in my browser I see my working Jupyter notebook server environment
on **worker**. 


First: **bastion** has a moving target public ip address. Each time I stop and re-start it the address 
changes. So I assign it a fixed (AWS: 'elastic ip') ip address.


Now to tunnel.

```
 $ ssh -i bastion.pem ubuntu@12.23.34.45
 ```
 
 Move `worker.pem` to bastion.
 
```
$ sftp -i bastion.pem ubuntu@12.23.34.45
sftp> put worker.pem
```

* Confirm can **`ssh`** to worker from laptop
* From laptop: `ssh ubuntu@12.23.34.45 -i bastion.pem`
* From bastion:
    * `ssh -i worker.pem ubuntu@10.0.1.234` (note use of private subnet ip address for worker)
    * On worker: `(jupyter notebook --no-browser --port=8889) &`
        * copy long token that looks like **`4109891ab3e0ec38c2aec9c427c8be11eda975ab2882a52a`**
    * Exit to bastion
    * `ssh -N -f -i worker.pem -L localhost:7005:localhost:8889 ubuntu@10.0.1.234`
        * This is the second part of the tunnel from bastion to worker
    * `exit` now back in bash on laptop
    * `ssh -N -f -i bastion.pem -L localhost:7004:localhost:7005 ubuntu@12.23.34.45`
    * laptop browser address bar enter `localhost:7004` and paste in token string
  
## Why use miniconda instead of anaconda?


[Read this.](https://www.educative.io/edpresso/anaconda-vs-miniconda)


## How do I monitor my CPU usage to make sure I'm firing on all cylinders?


Wes (an expert in cloud VM performance) says "Use **`top`** from your VM bash command line."


He continues: "Cloud watch metrics (AWS EC2 console GUI) are delayed, updated once every 5 minutes.
A localized spike in CPU use will take some time to display in the console. It is possible 
to pay for a higher sampling rate in the console...' (but why?)


## How do I keep my VM patched up to date?
