---
layout:     post
title:      "Getting started with git"
date:       2016-03-16 18:00:00
author:     "Apoorv Jagtap"
header-img: "images/git_tut.png"
---

<p> As the title of my blog suggests this tutorial is based on my understanding of git and mostly for my reference. For more in-depth information I would like to direct you to <a href="https://www.atlassian.com/git/tutorials/"</a> and the official git tutorial on <a href="https://try.github.io/levels/1/challenges/1"</a></p>
<p> Of course there are other sources which simplify the learning curve a lot. But honestly, I believe its not that difficult getting started and once on it I would say it's very difficult to live without it. </p>
<p> This guide will explain the basic commands required almost for every project. I will also add some commands to help with collaboration with other people. I would add commands and tips along the way, so check for any updates. </p>

# Getting started with basics

## Commands required for almost every project

* `git init` - As you might have guessed, this very first command initializes the git repository. Although not compulsory, it is a good practice to add `README.md` to help others understand the purpose of your project especially if it is open source.
---
* `git add` - Any new file you want to add to the project you are currently working on will have to be added with this command
---
* `git commit -m "Some useful message explaining the update"` - This is used when you are ready to commit the changes the made to your files included in the project. It is generally considered ideal to do it after making few updates, especially when updated particular part of the project, before moving to the next part.
---
* `git push origin master` - The above changes are only made available in the local repository, but not updated with the master branch. The advantage of this 2 step process to make changes to repository will become clear in the next section which goes over the collaboration benefits by git.
--- 
