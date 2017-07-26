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
(the following code is my whole .zshrc file)
```
# If you come from bash you might have to change your $PATH.
# export PATH=$HOME/bin:/usr/local/bin:$PATH

# Path to your oh-my-zsh installation.
export ZSH=/Users/steve/.oh-my-zsh

# Set name of the theme to load. Optionally, if you set this to "random"
# it'll load a random theme each time that oh-my-zsh is loaded.
# See https://github.com/robbyrussell/oh-my-zsh/wiki/Themes
ZSH_THEME="smcgee31"

# Uncomment the following line to use case-sensitive completion.
# CASE_SENSITIVE="true"

# Uncomment the following line to use hyphen-insensitive completion. Case
# sensitive completion must be off. _ and - will be interchangeable.
# HYPHEN_INSENSITIVE="true"

# Uncomment the following line to disable bi-weekly auto-update checks.
# DISABLE_AUTO_UPDATE="true"

# Uncomment the following line to change how often to auto-update (in days).
# export UPDATE_ZSH_DAYS=13

# Uncomment the following line to disable colors in ls.
# DISABLE_LS_COLORS="true"

# Uncomment the following line to disable auto-setting terminal title.
# DISABLE_AUTO_TITLE="true"

# Uncomment the following line to enable command auto-correction.
# ENABLE_CORRECTION="true"

# Uncomment the following line to display red dots whilst waiting for completion.
# COMPLETION_WAITING_DOTS="true"

# Uncomment the following line if you want to disable marking untracked files
# under VCS as dirty. This makes repository status check for large repositories
# much, much faster.
# DISABLE_UNTRACKED_FILES_DIRTY="true"

# Uncomment the following line if you want to change the command execution time
# stamp shown in the history command output.
# The optional three formats: "mm/dd/yyyy"|"dd.mm.yyyy"|"yyyy-mm-dd"
# HIST_STAMPS="mm/dd/yyyy"

# Would you like to use another custom folder than $ZSH/custom?
# ZSH_CUSTOM=/path/to/new-custom-folder

# Which plugins would you like to load? (plugins can be found in ~/.oh-my-zsh/plugins/*)
# Custom plugins may be added to ~/.oh-my-zsh/custom/plugins/
# Example format: plugins=(rails git textmate ruby lighthouse)
# Add wisely, as too many plugins slow down shell startup.
plugins=(git github colored-man colorize node npm nvm osx zsh-syntax-highlighting jira)

source $ZSH/oh-my-zsh.sh

# User configuration

# export MANPATH="/usr/local/man:$MANPATH"

# You may need to manually set your language environment
# export LANG=en_US.UTF-8

# Preferred editor for local and remote sessions
# if [[ -n $SSH_CONNECTION ]]; then
#   export EDITOR='vim'
# else
#   export EDITOR='mvim'
# fi

# Compilation flags
# export ARCHFLAGS="-arch x86_64"

# ssh
# export SSH_KEY_PATH="~/.ssh/rsa_id"

# Set personal aliases, overriding those provided by oh-my-zsh libs,
# plugins, and themes. Aliases can be placed here, though oh-my-zsh
# users are encouraged to define aliases within the ZSH_CUSTOM folder.
# For a full list of active aliases, run `alias`.
#
# Example aliases
# alias zshconfig="mate ~/.zshrc"
# alias ohmyzsh="mate ~/.oh-my-zsh"


# Load general aliases
alias cdls="cd ~/Documents/Developer/loan-service/"
alias cdjs="cd ~/Documents/Developer/journey-service/"
alias cdsp="cd ~/Documents/Developer/system-provisioning"
alias cdmg="cd ~/Documents/Developer/myGitStuff"
alias cdu="cd .."
alias c.="code ."
alias rmnmno="rm -rf node_modules/ && npm i --no-optional"
alias rmnm="rm -rf node_modules/ && npm i"


# Load git aliases
alias gs="git status"
alias ga="git add"
alias gaa="git add -A"
alias gc="git commit"
alias gcm="git commit -m"
alias gcq="git add -A && git commit -m 'quick commit'"
alias gco="git checkout"
alias gcob="git checkout -b"
alias gcom="git checkout master"
alias gp="git push"
alias gpf="git push --force-with-lease"
alias gpo="git push origin"
alias gd="git diff | mate"
alias gb="git branch -vv"
alias gba="git branch -a"
alias gbd="git branch -d"
alias gla="git la"
alias gd="git diff"
alias gstu="git stash -u"
alias gstp="git stash pop"
alias gl="git --no-pager log --oneline -10"
alias gl2="git --no-pager log --oneline -20"
alias gfa="git fetch --all"
alias gff="git merge --ff-only"


# Detect and use nvm
autoload -U add-zsh-hook
load-nvmrc() {
  local node_version="$(nvm version)"
  local nvmrc_path="$(nvm_find_nvmrc)"

  if [ -n "$nvmrc_path" ]; then
    local nvmrc_node_version=$(nvm version "$(cat "${nvmrc_path}")")

    if [ "$nvmrc_node_version" = "N/A" ]; then
      nvm install
    elif [ "$nvmrc_node_version" != "$node_version" ]; then
      nvm use
    fi
  elif [ "$node_version" != "$(nvm version default)" ]; then
    echo "Reverting to nvm default version"
    nvm use default
  fi
}
add-zsh-hook chpwd load-nvmrc
load-nvmrc


# tabtab source for serverless package
# uninstall by removing these lines or running `tabtab uninstall serverless`
[[ -f /Users/steve/Documents/Developer/system-provisioning/node_modules/tabtab/.completions/serverless.zsh ]] && . /Users/steve/Documents/Developer/system-provisioning/node_modules/tabtab/.completions/serverless.zsh
# tabtab source for sls package
# uninstall by removing these lines or running `tabtab uninstall sls`
[[ -f /Users/steve/Documents/Developer/system-provisioning/node_modules/tabtab/.completions/sls.zsh ]] && . /Users/steve/Documents/Developer/system-provisioning/node_modules/tabtab/.completions/sls.zsh
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






