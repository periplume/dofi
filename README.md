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
curl -O https://raw.githubusercontent.com/periplume/dofi/refs/heads/main/dofi
chmod +x dofi
./dofi install -h  # to view installation options
./dofi install     # to install with all defaults
```
#### option 2: use wget
```
wget -O dofi https://raw.githubusercontent.com/periplume/dofi/refs/heads/main/dofi
chmod +x dofi
./dofi install -h  # to view installation options
./dofi install     # to install with all defaults
```
#### option 2: use git
```
git clone https://github.com/periplume/dofi.git && cd dofi
./dofi install
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
note: use -h to for specific command options (eg 'dofi attach -h')

note: git commands may be used directly, eg:
$ dofi git status
~~~
---
~~~

usage: dofi install [OPTIONS]

summary: install the script and create the local repo

install options:
 -l               use ~/.local/bin
                    [default]
 -b               use ~/bin
 -u               do not update PATH
                    [default adds entry in .bashrc]
 -d               do not create local dofi repo
                    [default creates if no existing]
 -s <path>        specify location
 -n               do not offer pass option
                    [default offers pass inititialization]
~~~
---
~~~

usage: dofi attach [OPTIONS]

summary: add a remote repo, optionally creates the remote
on supported git hosting platforms

attach options:
 -p <platform>    remote platform <platform>
                    [tested platforms: github]
 -u <name>        use <name> as username
                    [default prompts for user name]
 -n <name>        specify the remote repo name
                    [default is 'dotdofi']
 -c               create the remote repo first
                    [supported platform: github]
                    [requires gh cli]
 -e               use empty ssh key passphrase
                    [default is to prompt for a passphrase]
 -s               create public (shared) repo
                    [default is private]
 -w               use https (web)
                    [default is ssh]
 -t               test attach conditions
                    [no changes will be made]
~~~
---
~~~

usage: dofi status [OPTIONS]

summary: print installation and repo status 

status options:
 -v               verbose
~~~
---
~~~

usage: dofi version [OPTIONS]

summary: print version information

version options:
 -c               check for updates
 -v               verbose
~~~
---
### description
~~~


statement of purpose (an apologia...of the platonic kind)

dofi is a single bash script designed to manage user dotfiles using the
git bare-repo method. it can be used, of course, to bring any files
under local git control. it is a prime example of scratching one's own
itch.

i've always wanted to manage my configurations better, but never found
the best way to do it without tinkering every time to make it work
again. its the simple things that break, like setting up authentication,
the things most people do rarely and scripts do poorly. i've taken the
time to circle the wagons as best as possible, and made an effort to
allow for extension within the framework of this script to amend what
i've missed.

the installation and interface is intended for users without prior
knowledge of linux, let alone git, although it does not preclude expert
git users. the user experience is meant to cater to non-technical users
and to conceal the complexities of git and data replication. ideally, my
mother should be capable of using it.

for data redundancy, it provides an easy to follow procedure to set up a
remote repo to which to replicate (github only for now), and there is
much more work to do to make the replication more robust. git, as it
turns out, is as fickle as your last girlfriend.

the code style sacrifices brevity for clarity; it aims to be robust,
honest, fail-safe and easy to read. obfuscation is not a noble goal;
just because you can compress 10+ simple lines into 3 complex ones
doesn't justify the sacrifice in readability (for normal humans,
including the one you will be when you look at your code in two years).
be mindful that even your own memory fades with time, and be forgiving
of this reality. its ok to explain your decisions, even when they seem
obvious now.

when it comes to the https vs ssh question (esp with regards to setting
up git remotes with github) we prefer ssh, despite the institutional
resistance. nevertheless, the validation and test routines here should
give some clue as to why this is difficult in the first place, before
one even attempts to securely manage these wonderful little tokens
https authentication requires. for now, the https routines are not
functional, although all the framework should be there to extend the
script to seamlessly support https without all the moving hurdles.

we do make sacrifices too. notice how we shield the user from some of
the "normal" security measures, like forcing the user to check the ssh
keys when first connecting to a new host. security is a fine line
between rigor and stupidity. does anyone really wonder why encryption
hasn't been widely adopted? if so, consult the man pages of these
subsystems. and for god's sake, be mindful of the user experience, it's
not that difficult.

the code also aims to be self-documenting self-building, in other words,
fully automated. this, it turns out, seems to be inversely difficult to
skill, in other words, the more you know, the less you struggle to do
the easy things, which renders your stuff elitist and sloppy. if you're
shooting to filter out the rest of us, bravo, but really, how often have
you just done the simple setup steps mindlessly and neglected to
incorporate them into the build process, forgetting that most of us
don't know these things?

for more info about the "devops" approach, consult the _build() function
within the dofi.build script. i'm not a programmer myself, although i've
been using linux for a long time. this is my first real "project", in
other words, i am an amateur, and my approach has been to find and write
good patterns that i can personally use and reuse. i suppose this
project is a demonstration of reference.

but really, this is just a wrapper for git, no more. git for non-git
users.
~~~
---

