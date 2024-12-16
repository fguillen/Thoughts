---
title: Developer new computer setup
description: List of steps to get the laptop ready for development
published: true
date: 2024-12-16T20:47:19.789Z
tags: 
editor: markdown
dateCreated: 2024-12-05T09:19:56.931Z
---

# OhMyZsh
```
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

## Prompt

```
brew install powerlevel10k
echo "source $(brew --prefix)/share/powerlevel10k/powerlevel10k.zsh-theme" >>~/.zshrc
exec zsh
```

# Brew
```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

# Docker

- https://docs.docker.com/desktop/install/mac-install/


## Dev Utils

```
xcode-select --install
brew install google-chrome
brew install postgresql
brew install redis
brew install dbeaver-community
brew install visual-studio-code
```

### Ruby

```
brew install rbenv
rbenv init
rbenv install --list
```

## User Utils

```
brew install 1password
brew install rectangle
brew install maccy
brew install grammarly-desktop
brew install krita
brew install vlc
brew install wine-stable
brew install spotify
```

## Extra libraries

```
brew install ffmpeg
brew install imagemagick
```

- https://handbrake.fr/
