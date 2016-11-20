---
layout: post
title: Command-Line - Vim Basics
---

<div class="message">
  Vim is essential when you come across a headless linux and need to edit a file.    
  Which you will, when you ssh onto a server machine for example.
</div>

So, you've probably been here:

> Everyone's first vim session. ^C^C^X^X^X^XquitqQ!qdammit[esc]qwertyuiopasdfghjkl;:xwhat

This is because vim isn't exactly intuitive to handle.    
But when you get the hang of it, it is a super handy tool to do some on-the-spot text editing.

### View Mode vs. Edit Mode

The first confusion is: Why can't I edit the text right when I enter vim?   

**You enter vim in View Mode.**

To **get to Edit Mode** simply type **i**   
Now you can edit text...   
To **get back to View Mode** from there type **[esc]** or **[Ctrl+C]**   
Now you can't edit text...

Now do this about 20 times, because that is the most important thing to know.

### So, what can I do in view mode?

In view mode, you can 
 - move around the document
 - copy, cut and paste
 - undo and redo
 - search text    

and lots more, but these are the basic things you need to know.

#### Moving around
By using the cursor keys you can move one character at a time.  
By pressing **w** you move to the **beginning of the next word**   
By pressing **b** you move to the **beginning of the previous word**   
By pressing **$** you move to the **end of the current line**  
By pressing **0 (zero)** you move to the **beginning of the current line**  
By pressing **G** you move to the **end of the document**  
By pressing **gg** you move to the **beginning of the document**   
By pressing **42G** you move to **line 42** of the document  
By pressing **[Ctrl+F]** you move **one page down**   
By pressing **[Ctrl+B]** you move **one page up**   

#### Copy, cut and paste
First, press **v** to enter Visual Mode.   
By moving the cursor as described above you select text.   
To **copy** text to the clipboard, press **y**    
To **cut** text to the clipboard, press **d**   
After this, you can **paste** the clipboard text by pressing either **p** (insert **after** cursor position) or **P** (insert **before** cursor position)

#### Undo and redo
To undo press **u**    
To redo press **[Ctrl+R]**

#### Search text
By typing **/wordyousearchfor** followed by [Enter] you jump to the **first occurence of "wordyousearchfor"** after the current cursor postition    
Now hit **n** to jump to the **next occurrence**

### Saving and quitting

To save a your changes **you need to be in View Mode**   
Type **:w** to **save your changes**.   
Type **:q** to **quit vim**   
You can't leave vim like this if you have unsaved changes.   
Type **:q!** to **leave vim and discard all changes**   
Type **:wq** to **save, then leave**   
Type **:w newfilename.txt** to **save as newfilename.txt**

### Wrapping up
This is only the tip of the iceberg, but I found that knowing these commands is what you really need to be productive with vim (and not be frustrated by it).   
And remember, repetition is the key...