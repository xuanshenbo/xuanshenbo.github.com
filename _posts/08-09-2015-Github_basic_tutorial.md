   
layout: post
title: "Github Basic Tutortial"
description: "This tutorial is made for SWEN222 project team members, however everyone can use it as a quick tutorial. It only has extremely basic operations."
category: Github
tags: [Github]
   
{% include JB/setup %}

This tutorial is made for SWEN222 project team members, however everyone can use it as a quick tutorial. It only has extremely basic operations.

<!--more-->

1. [Create a Java project in Eclipse] (#Create Project)
2. [Initialise your Git configuration for your project] (#Initialise Git)
3. [Pull the project] (#Pull)
4. [Make changes] (#Modify)
5. [Commit and push] (#Push)

#Create a Java project in Eclipse <a id="Create Project"></a>

**Note:**For simplicity I use Eclipse here as an example, feel free to use other IDEs or editors.

It should be straight forward I'm not gonna say anything here.

#Initialise your Git configuration for your project <a id="Initialise Git"></a>

Now, go to your ```src``` file under your project and type the following command:

```
git init
```

Now you should have created a hidden file ```.git/```. This means you have initialised your directory to a git directory.

To view all your files in the current directory type the command ```ls -a```. If you don't have a ```.git/``` file you did something wrong!

