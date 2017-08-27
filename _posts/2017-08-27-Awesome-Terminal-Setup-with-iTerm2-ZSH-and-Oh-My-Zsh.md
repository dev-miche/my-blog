---
layout: post
title: Awesome Terminal Setup with iTerm2, ZSH and Oh-My-Zsh
---

Are you bored with the default terminal of Mac? Want to turn your terminal into something more interactive and colorful? Well here is the iTerm2 and oh-my-zsh for rescue.

iTerm2 is a Mac OS terminal replacement, download it from [here](https://www.iterm2.com/downloads.html) or install it using ```homebrew``` by executing

```
brew install cask
brew cask install iterm2
```

[Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh) is an open source, a community-driven framework for managing your zsh configuration.

Let's utilize both to setup a customisable and interactive terminal development environment.

## Step 1: Install iTerm2

[Download](https://www.iterm2.com/downloads.html) and install the iTerm2.

Now change the default theme to ```Solarized Dark``` through

```
Iterm2 -> Preferences -> Profiles -> Colors
```

Select the ```Solarized Dark``` from the ```color presets``` drop-down menu. If ```Solarized Dark``` option is not available then download the theme through

```
cd ~/Downloads
wget https://raw.github.com/altercation/solarized/master/iterm2-colors-solarized/Solarized%20Dark.itermcolors
```
And then select the import option from the drop-down menu to import the theme.

There are few more tweaking we can do such as setting scroll back to unlimited and open existing file path in a text editor from the terminal by clicking on a link with command key.

#### Set an unlimited scroll back
```
Preferences -> Profiles -> Terminal
```
And check the unlimited scroll back option.

#### Select the editor for file opening

```
Preference -> Profile -> Advanced
```

In ```semantic history ``` select ```open with editor``` and select your choice of editor from the drop-down menu.

## Step 2: Install Zsh

Install zsh and zsh completions using homebrew

```
brew install zsh zsh-completions
```

## Step 3: Install oh-my-zsh

You can install this via the command-line with either curl or wget.

### via curl
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

### via wget
```
sh -c "$(wget https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
```

## Step 4: Basic configuration and install plugins

You can change the zsh configuration in ``` .zshrc``` file placed in the home directory. Open the ```.zshrc``` file in your choice of editor, I am using vi editor in the below example

```
cd
vi .zshrc
```
Find below line and set the theme to ```agnoster```

```
ZSH_THEME="agnoster"
```
Now reload the configuration file to reflect the changes

```
source ./.zshrc
```
If you find weird character on your terminal download and install [Meslo](https://github.com/powerline/fonts/blob/master/Meslo%20Slashed/Meslo%20LG%20M%20Regular%20for%20Powerline.ttf) font.

Now set iTerm2 to use this font through

```
Preference -> Profiles -> Text
```

Click on change font, from family drop-down select ```meslo LG M DZ for powerline``` with font size ```14```.

It seems weird to see your username prepended in display path, let's remove it.

Open ```.zshrc```

```
cd
vi .zshrc
```
Add following in the file

```
DEFAULT_USER=`whoami`
```

Let's install some useful plugins.

#### Install zsh-syntax-highlighting
[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) highlight the syntax with different colors.
```
brew install zsh-syntax-highlighting
```
Add in the end of  ```.zshrc```

```
source /usr/local/share/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
#### Install zsh-autosuggestions

[zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) suggest the command used in past. Use right arrow key to use command from the suggestion.

Clone the repo
```
cd
git clone git://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```
Then add ```zsh-autosuggestions``` in the plugins list inside ```.zshrc```

```
plugins=(zsh-autosuggestions)
```
Reload the configuration file

```
source ./.zshrc
```
Still, if you are not able to see the suggestion, add following line in the end of ```.zshrc```
```
ZSH_AUTOSUGGEST_HIGHLIGHT_STYLE='fg=white'
```
