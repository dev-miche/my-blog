---
layout: post
title: Exuberant Ctags
---

As per Wikipedia definition, Ctags is a programming tool that generates an index (or tag) file of names found in source and header files of various programming languages. Depending on the language, functions, variables, class members, macros and so on may be indexed. These tags allow definitions to be quickly and easily located by a text editor or other utility.

In other words, Ctags indexes a project’s classes, methods, etc in a file called tag. So we can navigate back and forth their declaration and definition in a code editor.

## Install Ctags
Install ctag using [Homebrew](https://brew.sh/) in OS X
```
brew install ctags
```
Or install in Ubuntu
```
sudo apt-get install exuberant-ctags
```
To ignore directories, add them in a ```.ctags``` file and place it in your home directory.

[This](https://github.com/dev-miche/dotfiles/blob/master/.ctags) is an example of my ```.ctags```.

## Vim Setup
For vim to find ```tags``` file, add the following in ```.vimrc```
```
set tags=./tags;
```
Generate ```tags``` in you project directory 
```
ctags -R .
```
## Create git hooks

Every time a change is made in any of the project files, we need to re generate the tags. We can create ```git hooks``` which will generate tags on add, commit, checkout, etc.

In your home directory 
```
mkdir -p ~/.git_template/hooks
git config --global init.templatedir '~/.git_template'
```
Either [download](https://github.com/dev-miche/dotfiles/tree/master/.git_template/hooks) the files and place them inside the ```hooks``` directory, or create the following files manually and make them executable.

```
touch ctags post-checkout post-commit post-merge post-rewrite pre-commit pre-push prepare-commit-msg
chmod u+x ctags post-checkout post-commit post-merge post-rewrite pre-commit pre-push prepare-commit-msg
```
Place the following script in ```ctags``` files.
```
#!/bin/sh
ctags -R --languages=ruby --exclude=.git --exclude=log . $(bundle list --paths)
```
Place the following script in ```post-checkout``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/post-checkout
[ -f "$local_hook" ] && . "$local_hook"
.git/hooks/ctags >/dev/null 2>&1 &
```
Place the following script in ```post-commit``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/post-commit
[ -f "$local_hook" ] && . "$local_hook"
.git/hooks/ctags >/dev/null 2>&1 &
```
Place the following script in ```post-merge``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/post-merge
[ -f "$local_hook" ] && . "$local_hook"
.git/hooks/ctags >/dev/null 2>&1 &
```
Place the following script in ```post-rewrite``` file.
```
#!/bin/sh
case "$1" in
  rebase) exec .git/hooks/post-merge ;;
esac
```
Place the following script in ```pre-commit``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/pre-commit
if [ -f "$local_hook" ]; then
  . "$local_hook"
fi
```
Place the following script in ```pre-push``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/pre-push
if [ -f "$local_hook" ]; then
  . "$local_hook"
fi
```
Place the following script in ```prepare-commit-msg``` file.
```
#!/bin/sh
local_hook="$HOME"/.git_template.local/hooks/prepare-commit-msg
if [ -f "$local_hook" ]; then
  . "$local_hook"
fi
```
