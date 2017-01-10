# macSetup
just some stuff for setting up my macbook
#
## Install Homebrew

[http://brew.sh/](http://brew.sh/)

## Install iTerm2

It's just a better terminal experience (seriously).

[https://www.iterm2.com/](https://www.iterm2.com/)

iTerm2 color schemes can be found [HERE](https://github.com/mbadolato/iTerm2-Color-Schemes/tree/master/schemes).

But you like [THIS ONE](https://github.com/mbadolato/iTerm2-Color-Schemes/blob/master/schemes/DimmedMonokai.itermcolors) in particular. (DimmedMonokai)
#
## Install zsh

We'll install `zsh` for all the features offered by `oh-my-zsh`. The installation and usage is really intutive.

Install zsh and zsh completions using homebrew
```
brew install zsh zsh-completions
```
Now you can customize your shell using Oh My Zsh.
#
## Install Oh-My-Zsh
Install oh-my-zsh on top of zsh to get additional functionality
```
curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
```
if you're still in the default shell, change default shell to zsh manually
```
chsh -s /usr/local/bin/zsh
```
edit the `.zshrc` by opening the file in a text editor (located in the root dir ~/.zshrc)
```
# This theme will have to be copied into the ~/.oh-my-zsh/themes directory to work
ZSH_THEME="smcgee31"

plugins=(git github colored-man colorize node npm nvm osx zsh-syntax-highlighting jira)

# Load general aliases (note that cddl is project specific and would change all the time?)
alias cddl="cd Documents/Developer/loan-service/"
alias c.="code ."

# Load git aliases
alias gs="git status"
alias ga="git add"
alias gaa="git add ."
alias gc="git commit"
alias gcm="git commit -m"
alias gco="git checkout"
alias gcob="git checkout -b"
alias gpl="git pull"
alias gplom="git pull origin master"
alias gp="git push"
alias gpo="git push origin"
alias gd="git diff | mate"
alias gb="git branch"
alias gba="git branch -a"
alias gbd="git branch -d"
```
#
## Install Visual Studio code

This is actually the best editor that I have used to far. I has great debugging features, integrated Terminal, and a Marketplace to get many other features. You'll love it, honestly.

Get the install file [HERE](https://code.visualstudio.com/)

Be sure to add the launch.json file for the debugger using the Node.js environment. Note that this is set up for Mocha.

Next add your Extentions from Marketplace. Current list:
* Align
* Angular 1 JavaScript and TypeScript Snippets
* Beautify css/sass/scss/less
* Debugger for Chrome
* Dimmed-monokai theme
* EditorConfig for VS Code
* ES6 Mocha Snippets
* HTML Snippets
* JavaScript (ES6) code Snippets
* JavaScript Snippet Pack
* One Monokai Theme
* vscode-icons
#
## Install Git and github
What's a developer without Git? To install, simply run:
```
brew install git
```
When done, to test that it installed fine you can run:
```
git --version
```
And running `which git` should output `/usr/local/bin/git`

Next copy and paste both the .gitconfig and the .gitignore_global files into the root directory..
This will setup your git name, email, aliases, and will set VS Code as your Git Mergetool, as well as the very important global gitignore.

Also don't forget the .gitignore_global file that has been included. This needs to be copied to the root directory also.
#
## SSH Config for Github
This might be difficult to configure in case you have two factor authentication enabled. Please use the SSH config in that case.

Setting up SSH is really simple as well. Most of the instructions below are referenced from here.

First, we need to check for existing SSH keys on your computer. Open up your Terminal and type:
```
$ cd ~/.ssh
$ ls -al
# Lists the files in your .ssh directory
```
Check the directory listing to see if you have files named either id_rsa.pub or id_dsa.pub. If you don't have either of those files go to step 2. Otherwise, you can skip to step 3.

Second, To generate a new SSH key, copy and paste the text below, making sure to substitute in your email. The default settings are preferred, so when you're asked to "enter a file in which to save the key,"" just press enter to continue.
```
$ ssh-keygen -t rsa -C "your_email@example.com"
# Creates a new ssh key, using the provided email as a label
# Generating public/private rsa key pair.
# Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
Please use a strong passphrase for your keys.

Third, Add your keys to Github by going into account settings.






