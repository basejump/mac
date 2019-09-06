# macOS Sierra v. 10.12 Setup 

[View a more detailed explanation of these steps here.](https://www.taniarascia.com/setting-up-a-brand-new-mac-for-development/) 

This is a simple list of instructions to make setting up your Apple computer as fast and efficient as possible for front end web development.

## Preferences

- **Keyboard > Text >** Disable "Correct spelling automatically".
- **Security and Privacy > Firewall >** On
- **Security and Privacy > General >** App Store and identified developers
- **File Sharing >** Off
- **Users & Groups > Login Items >** Spectacle, Flux

### Show Library folder

```shell
chflags nohidden ~/Library
```

### Show hidden files

This can also be done by pressing `command` + `shift` + `.`.

```shell
defaults write com.apple.finder AppleShowAllFiles YES
```

### Show path bar

```shell
defaults write com.apple.finder ShowPathbar -bool true
```

### Show status bar

```shell
defaults write com.apple.finder ShowStatusBar -bool true
```

## Homebrew

```shell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

### Mac App Store

```shell
brew install mas
```

## Multiple Users

if setting up mac for many users that will use brew see here
https://gist.github.com/jaibeee/9a4ea6aa9d428bc77925

#### Sign in
This may tell you if you already signed into the app store

```shell
mas signin email@email.com
```

### Brewfile

move the Brewfile here to home dir
```
brew bundle install
```

## Java

```shell
brew tap caskroom/versions
brew cask install java8
```

## SDK Man
see http://sdkman.io/install.html

```shell
curl -s "https://get.sdkman.io" | bash
```

```shell
sdk install grails
sdk install gradle
```

## GitHub

### Config - `~/.gitconfig`


```shell
[user]
	name = First Last
	email = email@email.com
[github]
	user = username
[alias]
	a = add
	ca = commit -a
	cam = commit -am
	s = status
	pom = push origin master
	pog = push origin gh-pages
	puom = pull origin master
	puog = pull origin gh-pages
	cob = checkout -b
[credential]
	helper = osxkeychain
```


## SSH

### Generate SSH key

```shell
ssh-keygen -t rsa -b 4096 -C "email@email.com"
```

### Config - `~./ssh/config`

For Sierra and High Sierra

```shell
Host *
 AddKeysToAgent yes
 UseKeychain yes
 IdentityFile ~/.ssh/id_rsa
```

### Copy to Github

```shell
pbcopy < ~/.ssh/id_rsa.pub
```
The add the key under your user settings on github https://github.com/settings/keys

see https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/
and https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/

## Bash

### Config - `~/.bash_profile`

```shell
alias brewup='brew update; brew upgrade; brew prune; brew cleanup; brew doctor'
```

```shell
source ~/.bash_profile
```

### Terminal Colors

```bash
export PS1="\[\033[36m\]\u\[\033[m\]@\[\033[32m\]\h:\[\033[33;1m\]\w\[\033[m\]\$ "
export CLICOLOR=1
export LSCOLORS=ExFxBxDxCxegedabagacad
```

## Node.js With NVM

### Install Nvm

```shell
curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.33.8/install.sh | bash
```

```shell
nvm install node
```

```shell
nvm use node
```

For later: how tou update node:

```shell
nvm install node --reinstall-packages-from=node
```

## Node Package Manager

### Gulp

```shell
npm install --global gulp-cli
```

## Ruby Version Manager

### Download rvm

```shell
\curl -sSL https://get.rvm.io | bash -s stable
```

### Install Ruby version

```shell
rvm install ruby-head
```

```shell
rvm --default use 2.4.0
```

```shell
gem install bundler
```

