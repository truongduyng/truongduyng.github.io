---
published: true
title: Vim basics
layout: post
author: Nguyen Truong Duy
category: Vim
tags: Vim
---

### Vim editor
Vim editor is a powerful editor, specialy working with server. You may love it.

### How to install it in Ubuntu
Run these command in terminal

```	sudo apt-get update	``` to make sure you have the updated sources.list. 
```	sudo apt-get install vim ``` to install vim.

### Open a file and do simple with it

1. Open a file and type something.

	``` vim path-to-file ``` to open a file on path-to-file with vim.

	In a standard editor, typing on the keyboard is enough to write something and see it on the screen. Not this time. Vim is in Normal mode. Let’s go to Insert mode. Type the letter i.

	You should feel a bit better. You can type letters like in a standard editor. To get back to Normal mode just press the ESC key.

2. Some commands in Normal mode of Vim

	You now know how to switch between Insert and Normal mode. And now, here are the commands that you need in order to survive in Normal mode:

	*	``` i ``` → Insert mode. Type ESC to return to Normal mode.
	* ``` x ``` → Delete the char under the cursor
	* ``` :wq ``` → Save and Quit (:w save, :q quit)
	* ``` dd ``` → Delete (and copy) the current line
	* ``` p ``` → Paste
	* ``` yy ``` → copy the current line, easier but equivalent to ddP.
	* ``` P ``` → paste before, remember p is paste after current position.
  * ``` u ``` → undo.
  * ``` <C-r> ``` → redo.
  * ``` :e ```: <path/to/file> → open
  * ``` :w ``` → save
  * ``` :saveas ```: <path/to/file> → save to <path/to/file>
  * ``` :x, ZZ or :wq ``` → save and quit (:x only save if necessary)
  * ``` :q! ``` → quit without saving, also: :qa! to quit even if there are modified hidden buffers.
  * ``` bn (resp. :bp) ``` → show next (resp. previous) file (buffer)

