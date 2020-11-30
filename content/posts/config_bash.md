---
title: Configure your shell
date: "2020-09-24"
template: "post"
draft: false
slug: "shell"
category: "Programming"
tags:
  - "Programming"
description: "Configure your terminal."
socialImage: "/media/42-line-bible.jpg"
---

Have you forgotten to activate your virtual environment before running your python application?

Have you forgotten to export your `env` variables before running the project?

This post is to solve that issue, you can automate the above mentioned whenever you are coming inside your project folder.

It doesn't matter, whether use `bash` or `zsh`, configuration is the same for both.

Here we are going to override the `cd` command, open your `.bashrc` or `.zshrc` file and paste the following command. Replace `{{string}}` with your folder name & replace `&& export DJANGO_READ_DOT_ENV_FILE=True && source /path/to/your/vir-env-folder/virenv-name/bin/activate` with your commands. 

```sh
function cd() { 
    builtin cd "$@"; 
    [[ "$PWD" =~ {{string}} ]] && export DJANGO_READ_DOT_ENV_FILE=True 
    && source /path/to/your/vir-env/bin/activate
}
```
After editing run, to get the changes
```sh
source .bashrc # for bash
source .zshrc # for zsh
```
Here I am exporting the environmental variables and activating the virtual environment when it comes to a particular folder.