# Mac Setup

## Xcode

### Install Xcode command line tool
```xcode-select --install```

### Install Xcode app
https://apps.apple.com/us/app/xcode/id497799835?mt=12


## Ruby via RVM
Install rvm and ruby
```bash
\curl -sSL https://get.rvm.io | bash -s stable --autolibs=homebrew --rails
```

```rvm autolibs packages```

## Homebrew

## Install python

```brew install python```
```brew install python@2```
```pip install --upgrade setuptools; pip install --upgrade pip```

Executable scripts from Python packages you install will be put in `/usr/local/share/python`, make sure it's on your PATH.


## Chrome
```brew cask install google-chrome```

backed up pro
files from `~/Library/ApplicationSupport/Google/Chrome`
go to `chrome://version/` in chrome and it will tell you which profile number the profile is for

## iTerm2
1, ```brew cask install iterm2```  
2. import settings from [here](./iterm/com.googlecode.iterm2.plist)


## Fonts

```bash
brew cask install font-hack-nerd-font 
brew cask install font-meslo-for-powerline 
brew cask install font-fontawesome  
brew cask install font-menlo-for-powerline 
brew cask install font-source-code-pro  
```    

## Bash It

```bash
git clone --depth=1 https://github.com/Bash-it/bash-it.git ~/.bash_it;
~/.bash_it/install.sh
```
Theme `brainy`

Add to bash_profile
`CLICOLOR=1`

## Bash Completion
```brew install bash-completion```

For it to work, add this to your ~/.bash_profile:
```bash
[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion
```

Or simply type:

```bash
echo "[ -f /usr/local/etc/bash_completion ] && . /usr/local/etc/bash_completion" >> ~/.bash_profile
```

## Install zsh and oh-my-zsh

```bash
brew install zsh
```

### Install oh-my-zsh
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### Install powerlevel10k	
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Set `ZSH_THEME=powerlevel10k/powerlevel10k` in your ~/.zshrc.
run `powerlevel10_prompt_configuration`

https://sourabhbajaj.com/mac-setup/iTerm/zsh.html

### Zsh Plugins
```bash
plugins=(git colored-man colorize pip python brew osx zsh-syntax-highlighting zsh-autosuggestions)
```

### prezto
```bash
git clone --recursive https://github.com/sorin-ionescu/prezto.git "${ZDOTDIR:-$HOME}/.zprezto”
```

```bash
setopt EXTENDED_GLOB
for rcfile in "${ZDOTDIR:-$HOME}"/.zprezto/runcoms/^README.md(.N); do
    ln -s "$rcfile" "${ZDOTDIR:-$HOME}/.${rcfile:t}"
  done
```


## Extras

### tree
```brew install tree```


### fzf
```brew install fzf;/usr/local/opt/fzf/install```

### ack 
```brew install ack```

### autojump
`brew install autojump`

## Setup vim
`brew install vim`

### awesome vim
```bash
git clone https://github.com/amix/vimrc.git ~/.vim_runtime
sh ~/.vim_runtime/install_awesome_vimrc.sh
```

Alias for updating script
```bash
alias updatevimruntime='cd ~/.vim_runtime && git pull --rebase && cd -'
```

### maximum-awesome
```bash
git clone https://github.com/square/maximum-awesome.git
cd maximum-awesome
rake
```

## Sublime
install from dmg file backed up or
```bash
brew cask install sublime-text
```

``ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl```

### Preferences
```json
{
    "auto_complete_delay": 5,
    "auto_complete_selector": "source, text",
    "color_scheme": "Packages/User/Monokai (SL).tmTheme",
    "create_window_at_startup": false,
    "folder_exclude_patterns":
    [
        ".svn",
        ".git",
        ".DS_Store",
        "__pycache__",
        "*.pyc",
        "*.pyo",
        "*.exe",
        "*.dll",
        "*.obj",
        "*.o",
        "*.a",
        "*.lib",
        "*.so",
        "*.dylib",
        "*.ncb",
        "*.sdf",
        "*.suo",
        "*.pdb",
        "*.idb",
        "*.psd"
    ],
    "font_face": "Source Code Pro",
    "font_size": 13,
    "ignored_packages":
    [
        "Markdown",
        "Vintage"
    ],
    "open_files_in_new_window": false,
    "rulers":
    [
        80
    ],
    "translate_tabs_to_spaces": true,
    "word_wrap": true
}
```

### Sublime package control
https://packagecontrol.io/installation

### Sublime linter
https://sourabhbajaj.com/mac-setup/SublimeText/SublimeLinter.html


## Install git
$ `brew install git`

```bash
git config --global user.name “Christopher Chen”;
git config --global user.email “chrichen@paypal.com”;
```

## Github
- Create token to add to IntelliJ
- create ssh key and add to GitHub for personal and work

### SSH Config for GitHub
The instructions below are referenced from the official documentation.

### Check for existing SSH keys
First, we need to check for existing SSH keys on your computer. We do this by running:
```$ ls -al ~/.ssh```

### Lists the files in your .ssh directory, if they exist
Check the directory listing to see if you have files named either id_rsa.pub or id_dsa.pub. If you don't have either of those files then read on, otherwise skip the next section.
### Generate a new SSH key
If you don't have an SSH key you need to generate one. To do that you need to run the commands below, and make sure to substitute the placeholder with your email. The default settings are preferred, so when you're asked to "enter a file in which to save the key,"" just press Enter to continue.
`ssh-keygen -t rsa -C "chrichen@paypal.com"`
Add your SSH key to the ssh-agent
Run the following commands to add your SSH key to the ssh-agent.
`eval "$(ssh-agent -s)"`

If you're running macOS Sierra 10.12.2 or later, you will need to modify your ~/.ssh/config file to automatically load keys into the ssh-agent and store passphrases in your keychain:
```bash
Host *
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/id_rsa
```
No matter what operating system version you run you need to run this command to complete this step:
`ssh-add -K ~/.ssh/id_rsa`

Adding a new SSH key to your GitHub account
The last step is to let GitHub know about your SSH key. Run this command to copy your key to your clipboard:
`pbcopy < ~/.ssh/id_rsa.pub`

Then go to GitHub and input your new SSH key. Paste your key in the "Key" textbox and pick a name that represents the computer you're currently using.


## Node and NPM via NVM 

### Install nvm 
```bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.35.1/install.sh | bash
```

### Install node
```bash
nvm install node; nvm install 8; nvm install 10;nvm install-latest-npm;nvm alias default node
```

### .nvmrc
You can create a .nvmrc file containing a node version number (or any other string that nvm understands; see nvm --help for details) in the project root directory (or any parent directory). Afterwards, nvm use, nvm install, nvm exec, nvm run, and nvm which will use the version specified in the .nvmrc file if no version is supplied on the command line.

For example, to make nvm default to the latest 5.9 release, the latest LTS version, or the latest node version for the current directory:

$ echo "5.9" > .nvmrc

$ echo "lts/*" > .nvmrc # to default to the latest LTS version

$ echo "node" > .nvmrc # to default to the latest version
Then when you run nvm:

$ nvm use
Found '/path/to/project/.nvmrc' with version <5.9>
Now using node v5.9.1 (npm v3.7.3)
nvm use et. al. will traverse directory structure upwards from the current directory looking for the .nvmrc file. In other words, running nvm use et. al. in any subdirectory of a directory with an .nvmrc will result in that .nvmrc being utilized.

The contents of a .nvmrc file must be the <version> (as described by nvm --help) followed by a newline. No trailing spaces are allowed, and the trailing newline is required.


## Install java and maven
https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

1.8: 
```bash 
 brew cask install adoptopenjdk/openjdk/adoptopenjdk8
 brew cask install homebrew/cask-versions/adoptopenjdk88
```

latest: 
```bash
brew cask install java
```

```bash
brew install maven
```

## Install Kafka

```brew install Kafka```


## Install IntelliJ
import settings from repo


## Install docker
```brew cask install docker```


## VSCode
```bash
brew cask install visual-studio-code
```

Open the Command Palette (F1) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.

use settings sync extension and download settings


## Install color schemes
in setup


## Last Pass
https://apps.apple.com/us/app/lastpass/id926036361?ls=1&mt=12
	    

## Spectacle

```brew cask install spectacle```

## Amethyst
```brew cask install amethyst```


## Others


## Spectacle

```bash
brew cask install spectacle
```

* Update all major combinations to work with Shift + Control + 1-9
* Remove the key combinations for the other sizes
* System Preferences -> Security and Privacy -> Accessibility -> Check


## Gimp
``brew cask install gimp``

## Authy Desktop
```brew cask install authy```

## Alfred
```brew cask install alfred```

## Total Finder
https://totalfinder.binaryage.com/

## Notebooks2
```dmg file in setup folder```
Set the default directory to a folder inside Dropbox for CloudSync
Overwrite one of the themes in the app with GitHub Mardown CSS

## Cheatsheet
```brew cask install cheatsheet```

## Timeout
take breaks
https://www.dejal.com/timeout/

## Tomighty
http://www.tomighty.org/
Tomighty is a desktop timer specifically designed for the Pomodoro Technique®. It's a software created and developed by Célio Cidral Junior, licensed to you under the Apache License 2.0. It’s free (gratis) and open source.

### Pomodoro Technique
The Pomodoro Technique® is a very simple and effective time management technique that helps you keep focused on tasks that require long periods of concentration. Read more about it at the official website.

Pomodoro Technique® and Pomodoro™ are registered and filed trademarks owned by Francesco Cirillo. Tomighty is not affiliated by, associated with nor endorsed by Francesco Cirillo.


Reference
----
Found this guy along the way:o [https://sourabhbajaj.com/mac-setup/](https://sourabhbajaj.com/mac-setup/)