---
title: This is a subpage
description: 
published: true
date: 2024-12-05T09:11:26.515Z
tags: 
editor: markdown
dateCreated: 2024-12-04T08:03:27.820Z
---

# How to install mysql2 gem in Mac

From: https://gist.github.com/fernandoaleman/385aad12a18fe50cf5fd1e988e76fd63

## Problem
Installing mysql2 gem errors on Apple silicon M1, M2 or M3 Mac running macOS Sonoma.

## Solution
Make sure mysql-client, openssl and zstd are installed on Mac via Homebrew.

> Replace mysql-client with whichever mysql package you are using

```
brew install mysql-client openssl zstd
```

### Install mysql2 gem.

> Replace 0.5.2 with whichever version you are using

```
gem install mysql2 -v '0.5.2' -- --with-mysql-lib=$(brew --prefix mysql-client)/lib --with-mysql-dir=$(brew --prefix mysql-client) --with-mysql-config=$(brew --prefix mysql-client)/bin/mysql_config --with-mysql-include=$(brew --prefix mysql-client)/include --with-ldflags="-L$(brew --prefix zstd)/lib -L$(brew --prefix openssl)/lib -L$(brew --prefix zlib)/lib" --with-cppflags="-I$(brew --prefix openssl)/include -I$(brew --prefix zlib)/include"
```