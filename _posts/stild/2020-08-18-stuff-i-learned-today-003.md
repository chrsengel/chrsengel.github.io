---
title: Stuff I learned today 003
date: 2020-08-19 22:49:00 +0200
categories: [stuff i learned today]
tags: [stild, regex, linux]
---

Today's post only has two entries about a neat feature I discovered in Studio Code and some helpful Linux commands

# RegEx In Studio Code

As many other developers nowadays[^dev-survey] I primarily use Studio Code for most of my projects. Today I found out that it natively supports regular expressions for Find/Replace operations. I stumbled over this as I tried to remove some items from multiple large xml files.

To use it, simply activate the regex icon in the menu popup (or hit `Alt + r`). The feature has great documentation[^studio-doc] but if you're used to regular expressions you are good go.

![Studio Code Regex](/assets/img/stild/2020/08-19/code-regex.png)

This really comes in handy if, for whatever reason, you have to use Windows and don't have access to `sed`.

# Linux stuff

## yes

I found a super helpful Linux tool, called `yes`. By default, all it does is output a line with `'y'`. You can also set another string. `yes` comes in really handy if you are using any kind of setup script that repeatedly requires an input. Just pipe the yes command into the script and you are done!

`yes | some_other_stuff`

## nmcli

In my home I have multiple different WIFI hotspots and so far I have not managed to get Ubuntu to automatically switch to the one with the best signal. So I usually do it by hand. However I do not like the GUI experience in Ubuntu. Everything still seems buggy and takes way longer than it should. So I researched online and found the `nmcli`[^nmcli] command that does the job.

The command `nmcli c ip <hotspot name>` will connect your system with the specified hotspot if available. In my experience this is way faster than using the GUI option. So I wrote a couple of one-liner scripts for each hotspot, like the following:

```bash
#!/bin/bash
nmcli c up "Obi-Lan Kenobi"
```

# Footnotes

[^dev-survey]: [Stackoverflow Dev Survey](https://insights.stackoverflow.com/survey/2019#technology-_-most-popular-development-environments)
[^studio-doc]: [Microsoft RegEx Docs](https://docs.microsoft.com/en-us/visualstudio/ide/using-regular-expressions-in-visual-studio?view=vs-2019)
[^nmcli]: [`nmcli` Manual](https://developer.gnome.org/NetworkManager/stable/nmcli.html)
