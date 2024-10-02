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
- tested on ubuntu 24.01.01
---
### usage
~~~

usage: dofi [GLOBAL OPTIONS] <command> [COMMAND OPTIONS]

summary: preserve, protect, and revision your personal files

global options:
 -h       print help
 -d       print debug messages
 -v       print version
 -e       print explaination

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

summary: install the script and create the local bare repo

install options:
 -h               print install usage
 -l               use ~/.local/bin
                    [default]
 -b               use ~/bin
 -u               update PATH in .bashrc
                    [default reports only]
 -d               do not create local dofi repo
                    [default creates if no existing]
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

usage: dofi status [OPTIONS]

summary: print installation and repo status 

status options:
 -h               print status usage
 -v               verbose
~~~
---
~~~

usage: dofi version [OPTIONS]

summary: print version information

version options:
 -h               print version usage
 -c               check for updates
 -v               verbose
~~~
---
### description
~~~

dofi is a single bash script designed to manage user dotfiles using
the git bare-repo method. it can be used, of course, to bring any
files under local git control.

the installation and interface is intended for users without prior
knowledge of git, although it does not preclude expert git users.

for data redundancy, it provides an easy to follow procedure to
set up a remote repo to which to replicate (github only for now).

the code style sacrifices brevity for clarity; it aims to be
robust, fail-safe and easy to read. obfuscation is not the goal.

the user experience is meant to cater to non-technical users and
to conceal the complexities of git and data replication. ideally,
my mother should be capable of using it.

the code also aims to be self-documenting self-building. for more
info, consult the _build() function within the dofi.build script.

# inspired in part by https://news.ycombinator.com/item?id=11070797
# and https://www.atlassian.com/git/tutorials/dotfiles
# and many other terminal-only projects.
~~~
---

