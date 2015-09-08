   
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
6. [In the future] (#Future)

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

Now go ahead and type the following command:
```
git remote add origin https://github.com/xuanshenbo/Test-Github
```

**Note:** The reason why we init our directory at the ```src``` file not the project is because the project directory contains a bunch of configurations for IDEs and also bin files. Since we don't want to mess up others' IDEs and we are only interested in the source files in our case, ```src``` would be a better place for us. So make sure all your source code including images are under your ```src``` file.

#Pull the project <a id="Pull"></a>

I have created a project for us:

<a href="https://github.com/xuanshenbo/Test-Github"> Test-Github</a>

Now under you ```src``` directory, type the following command:

```
git pull https://github.com/xuanshenbo/Test-Github
```

Now refresh your project in your Eclipse you will see a test package.

#Make changes <a id="Modify"></a>

Feel free to modify the class named after you. Please do not modify others' classes at this stage because we don't want to deal with conflicts. Actually this tutorial will not cover conflicts we will talk about this in our group meeting.

If you are not in our group, feel free to create a class named after yourself.

#Commit and Push <a id="Push"></a>

**NOTE:** Before doing this step, make sure you are one of the collaborators of the project. You need to email me your log-in name so I can add you as a collaborator.

Now type the following command:
```
git add .
```
where . means all

And then:
```
git commit -m "comment message"
```
make sure your comment message is clear and sensable. **IT WILL BE MARKED FOR THE PROJECT!!!**

Then:
```
git push -u origin master
```

Now it will ask for your username and password, after that you are done!

#In the future <a id="Future"></a>

Since we had done the initilisation part, in the future we will mainly be using the pull and push part. It is pretty much like the first time only that when you do the ```git push -u origin master``` part, you don't have to type the whole thing, ```git push``` will do.
