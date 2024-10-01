## dofi: dotfile manager

dofi takes the *git out* of bare-repo dotfile management
- a bash script with minimal dependencies
- automates the creation of the local dotfile repo
- automates and assists with the creation and connection to a remote repo
- friendly and easy introduction to dotfile management with git
- hides complexity at the expense of brevity (intentional design)
- attempts to be robust, clean, clear, and reusable code
- solves a simple problem: keep my stuff safe without hassle

---
### installation options
#### option 1: use curl
```
curl https://raw.githubusercontent.com/periplume/dofi/refs/heads/main/dofi
chmod +x dofi
./dofi install
```
#### option 2: use git to clone the dofi repo
```
git clone https://github.com/periplume/dofi.git
cd dofi; ./dofi install
```
---
### support
tested on ubuntu 24.01.01
---
### usage
---
~~~

usage: dofi [GLOBAL OPTIONS] <command> [COMMAND OPTIONS]

summary: preserve, protect, and revision your personal files

global options:
 -h       print help
 -d       print debug messages
 -v       print version

commands:
 add <file>       add file to the dotfile repo
 remove <file>    remove a file from the repo
 save             commit and push to the remote
 status           print summary of file and syncronization status
 attach           attach a new remote repo to push to
 connect          connect and pull from an existing dofi repo
 install          install dofi script and create local repo
 version          print script version details
note: use -h to for specific command options (eg 'attach -h')

note: git commands may be used directly, eg:
$ dofi git status
~~~
---
~~~

usage: dofi install [OPTIONS]

summary: copy the script into the designated PATH location

install options:
 -h               print install usage
 -l               use ~/.local/bin              [default]
 -b               use ~/bin
 -u               update PATH in .bashrc        [default reports only]
 -d               do not create local dofi repo [default creates]
 -s <path>        specify location
~~~
---
~~~

usage: dofi attach [OPTIONS]

summary: add a remote repo, optionally creates the remote
on supported git hosting platforms

attach options:
 -h               print attach usage
 -p <platform>    remote platform <platform>
                    [tested platforms: github]
 -c               create the remote repo
                    [supported platform: github]
                    [requires gh cli]
 -s               use ssh protocol
                    [default is https]
 -e               use empty ssh key passphrase
                    [default is to prompt for a passphrase]
 -n <name>        specify the remote repo name
                    [default is 'dotdofi']
~~~
---
~~~

[38;5;2mINFO[0m dofi is installed in /home/jason/.dofi
~~~
---
~~~

usage: dofi version [OPTIONS]

summary: print version information

build options:
 -h               print version usage
 -c               check for updates
 -v               verbose
 -b               print the build hash
~~~
---

