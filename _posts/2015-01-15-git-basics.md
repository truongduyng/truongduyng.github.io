---
published: true
title: Git and Github basics
layout: post
author: Duy
category: Git
tags: Git

---

### Git is a version control system.

Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.

Git is easy to learn and has a tiny footprint with lightning fast performance. It outclasses SCM tools like Subversion, CVS, Perforce, and ClearCase with features like cheap local branching, convenient staging areas, and multiple workflows.

### Github
Github is a code host, a place to share with everybody. It uses git. Creating a account very easily. Let's do it!

### How to use git in Ubuntu

#### Installion

On Ubuntu and similar systems you can install the Git command line tool via the following command:

```
sudo apt-get install git
```

#### Basic usage of git and github

1. First step: Creating a Repo in GitHub

Log in Github and create a repository. Just new and give it a name. For examples: demorepo

2. Second step: Config Git

	Open terminal and run these command to configure the user which will be used by Git.

	```
	git config --global user.name "Your username"
	```


	```
	git config --global user.email "Your.email@example.org"
	```

3. Third step: init, commit and push your project to github'repo
	On terminal, run these command:

	```
	git init
	```

	: Initialized git


	```
	git add .
	```

	: Add all files in folder to git

	```
	git remote add origin https://github.com/ntduy/demo.git
	```

	: choose repo to work.

	```
	git commit -m "Your message"
	```

	: Commit with your message. Your files are not on github now.

	```
	git push -u origin master
	```

	: push or up files to GitHub's repo using your user.

Thanks for reading! :)





