---
title: Git hooks
date: "2020-10-19"
template: "post"
draft: false
slug: "git-hooks"
category: "Programming"
tags:
  - "Programming"
  - "Git"
description: "Run your test cases before committing your code"
socialImage: "/media/42-line-bible.jpg"
---


Hello developers, have you committed the code without executing, I know you might be overconfident something like this

> Hey, this is just one line or one character change how can it break the system or fail from running the code.

In `python`, you might have missed the indentation or in the `java`, you might have missed the semicolon.

### What are git hooks?

Here comes the savior, git hooks we can configure the git commands to sneak into your code and ask to check whether my code is running or all my test cases are passed or do whatever you wanted to do.

### Where it will present?

Have you even gone inside the `.git` folder in your git repo, most likely it will be hidden. 

```bash
cd .git/hooks
ls
```

You can see the following files

```bash
applypatch-msg.commit-msg.sample
fsmonitor-watchman.post-update.pre-applypatch.pre-commit
pre-commit.pre-merge-commit.sample
prepare-commit-msg.sample
pre-rebase.pre-receive.sample
update.sample
```

### Let's see how to configure

Make sure you give enough permissions

execute the following command inside your git folder

```bash
chmod ug+x .git/hooks/*
```

> Or else you might get the following warning

```bash
hint: The '.git/hooks/pre-commit' hook was ignored because it's not set as executable.
hint: You can disable this warning with git config advice.ignoredHook false.
```

Good thing about hooks is we can configure in python as well as bash scripts, I am going to configure with python

Inside the hooks folder, create a file `pre-commit` 

```jsx
#!/usr/bin/env python3
import sys, os
print("checking before commiting")
ret = os.system('python manage.py test --settings=config.settings.local')
#print("---------------------------------",ret)
if(ret==0):
    print("------------ success test case and code passed --------------------")
    sys.exit(0)
else:
    sys.exit(1)
```

This will run the Django server and executes the test cases before committing the code to the git