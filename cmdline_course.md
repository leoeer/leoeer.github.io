---
layout: default
---

# What is this Command-Line Course?  
  
Command-Line Course ([KIK-LG218](https://courses.helsinki.fi/fi/kik-lg218/126710126)) is an online course at the University of Helsinki. The idea of the course is to teach students to operate and navigate in the UNIX environment. The course consists of weekly quizzes which go through the basic commands and tasks one should know when working with code, programming, language technology etc.  
Here are some of the topics we have learned about during the course:  

 * Navigating the UNIX system
 * Basics of file permissions
 * How to process text corpora
 * Regular Expressions
 * Text editor usage
 * How to create and run our own scripts
 * Customizing the bash environment
 * Installing programs from source
 * Version control using Git
 * Building webpages with GitHub Pages  

You can read more about the topics and my progress on the course below.

![ ](/assets/img/code.jpg)

### Week 1: Introduction to Command-Line Environments  
  
During the first week, we started with the very basics. We learned what text editors can be used for, and how text files and binary files differ. We were introduced to basic UNIX commands like `cat, less, ls, nano, touch, man, mv, cp, wget` and many more. File types were also discussed and we learned e.g. that not all files have a file extension in the Linux system. We also had our first touch with modifying a [_Project Gutenberg_][guten] book using the `nano` text editor.   
  
In my opinion the first week wasn't difficult at all, possibly because I had already gotten a peek at the UNIX world on a previous course. Although I think that this week was really useful and crucial to learning the more advanced things later down the road. I can imagine someone who has never done anything command-line related finding this week particularly useful (and even a little scary maybe). Overall I think Week 1 was a very good introduction to the topic and to the course, with the support of the first lecture where we got a great presentation which explained how computers work in general.  
  
I will be giving an example of some code correlating to the subject of each week. For example, during Week 1 we learned that the following command can be used to create a new file:  
  
`touch FILENAME`  
  


  
### Week 2: Navigating a UNIX system  
  
The second week was about learning how different file permissions effect their usage. We also got to extend our understanding about the structure of the UNIX file system and the working principles behind it. `sudo` command was introduced, and we got to know what it means to do commit changes as the root user. It was demonstrated to us that for example the commands we used in Week 1 (`ls, cp, nano` etc.) are in fact programs working our system, and by using the commands we have learned we actually just tell these programs what to do. We also learned how to change the permissions of files and directories and how to determine who gets to view, edit and execute them. In addition to these subjects, we studied and learned how symbolic links can be created and how they behave.  
  
The most useful command I learned how to use this week was deifinitely `chmod`. `chmod` is used to change the mode of a file with options and permissions. Since permissions are divided into three categories based on:  
  
1. What the user of the file is allowed to do
2. What a member of your group is allowed to do
3. What all others are allowed to do  
  
These are defined using the options 1 = _u_, 2 = _g_ and 3 = _o_. _a_ can be used if we want to give all these groups the same rights. Read, write and execute rights are referred to with the letters `r, w` and `x`. The following command would give read rights to everyone.  
> `chmod u=r, g=r, o=r myfile`  
or  
> `chmod a=r myfile`  
  
If we want to make no changes to previous rights and only add a read permission for example, we can use `a+r` instead of `a=r`.  
  
`chmod` can also be used with octal values (e.g. `chmod 777 myfile`). Each number gives permissions to _u, g and o._ These numbers are calculated using the values given to each permission:  
  
| Octal value | Permissions | Description          |
|-------------|-------------|----------------------|
|      0      |     ---     |    No permissions    |
|      1      |     --x     |     Execute only     |
|      2      |     -w-     |      Write only      |
|      3      |     -wx     |   Write and execute  |
|      4      |     r--     |       Read only      |
|      5      |     r-x     |   Read and execute   |
|      6      |     rw-     |    Read and write    |
|      7      |     rwx     | Read, write, execute |  
  
[Source of table](https://docs.oracle.com/cd/E19455-01/805-7229/6j6q8svd8/index.html)  

  
  
  
### Week 3: Corpus Processing  
  
In the beginning of Week 3 we learned to pipe standard output and commands. Piping basically means taking the result of the first command and forwarding the result to the next command. This opened a world of new possibilites to us, since we were no longer prisoners of using single commands like `less` on the command line. Now we could for instance use the command `echo` and pipe the result in to `less`, which gave us freedom to try all sorts of commands without cluttering the command line, which can happen very easily in text processing.   
  
In week 3 we got a taste of actual [NLP](https://en.wikipedia.org/wiki/Natural_language_processing). We started by using the command `grep` to search for words in texts and using `tr` and `sed` to replace words in text. And not just words, we also learned how to convert large text files (such as the [Life of Bee book][bee] in to sentence-per-line format to make text processing easier. We also learned how to generate frequency lists to see the most frequent words in a text file. I thought this was a very cool and useful thing.  
  
Week 3 was probably the most frustrating one for me, since I had some trouble with regular expressions. I did learn how to use them for searching things in corpora, but it was always a pain to see that my answers were not correct in the week's Quiz. For instance, I used the following regular expression to search for instances of the word "queen" in the [Life of Bee book][bee] (`wc -l` is used for counting the number of matching lines):  
  
```
> grep -Eo "(\bqueen\b[^\w-])" life_of_bee.sent | wc -l  
> 136  
```  
  
The `"(\bqueen\b[^\w-])"` regex is formed so that `\b` are used as word boundaries to express that we want to find words only in this form, and not for example "queens". `[^\w]` is used to exclude the hyphen (-), so that words like queen-bee are left out. Regex is very sensitive to mistakes, and that's why it can be frustrating from time to time.  
  

  


### Week 4: Scripting and UNIX Configuration Files  
  
During Week 4 we learned what UNIX environment variables are and how customizing them is sometimes necessary to make bash run things correctly. For me, this meant that for starters I had to learn how to make my bash start the newest version of **nano** instead of the original old version, which was unable to work some of the exercises we made. After this, we got to customize our own **.bashrc** configuration files, which give us the freedom to personalize our terminal view. Finally we got into writing scripts. Scripts are basically automated sets of commands written into files. They make working on the command like whole lot easier, and actually, they are a vital part for computers to work.  
  
For me the best thing in this week was the time when I finally figured out how to use `if` variables in a script. I created a script, which converts a text file into sentence-per-line format and if the process is succesfull, it lets the user know. I also included an error message and made it so that the script doesn't output any progress messages which are not relevant to the user. It looks like this:  
> [#! /bin/bash # script: myscript.sh...](/assets/documents/myscript.txt)  

  


### Week 5: Installing and Running Programs  
  
In my honest opinion, I didn't really enjoy Week 5. We learned how different libraries are installed (Java, Python, C) and how to code is compiled. We got familiar with `make` and _Makefile_ which are used to build other programs, libraries and projects. I had some trouble understanding the use of _Makefile_ variables. (If you think you are good at explaining them, please send me a message through my [contact channels](/index.html)!)
  
For Week 5 we did get to install and use some Python modules, which I thought were very useful. We used Bllipparser to parse text, and used the _guess_language_ module to guess some unknown languages which I thought was fun. Here's an example of an exercise we did using the _guess_language_ module:  

```
>$ python3
Python 3.7.1 (default, Nov  6 2018, 18:45:35) 
[Clang 10.0.0 (clang-1000.11.45.5)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> from guess_language import guess_language

>>> guess_language("This is an English sentence if I ever saw one.")  
'en'  
```  
  



### Week 6: Version Control  
  
_git_. Week 6 introduced _git_ to us. It's a version controlling "environment" one could say. _git_ allows you to make a repository of your project (directory) to your GitHub account, where you can share it with others and lots of other cool stuff. _git_ works as sort of a backup to your project, where you can make sure that the parts of your project which already function are not afflicted by new changes you make to your project. This is a huge help in big projects and in coding in general, where even a small typo can ruin a lot of things. You can make sure that your project stays functional while you're developing new features to it, and if you f*** things up, you can always return to your previous version. 

I really found _git_ useful, and can't wait to learn how to do more complicated things with it. Here's an example of my latest _git_ push (pushing means pushing changes made in my local repository to my GitHub repository) as I'm writing this project:  
  
```
>[leo@~/Documents/HY/cmdline_course/final/leoeer.github.io]==>: git log  
>commit b986f341c6d3a3ab92850abd0de08exxxxxxxxxx (HEAD -> cmdline-course, origin/cmdline-course)  
>Author: Leo Eerolainen lxx.exxxxxxxx@hxxxxxxx.fx  
>Date:   Wed Dec 19 13:21:49 2018 +0200  
>backup push after week3
```    
  
The log is longer in reality, but here I demonstrate that you can see recent activity between repositories and track changes.  

  


### Week 7: Building Webpages using GitHub Pages  
  
In Week 7 we learned about building webpages. We learned how to use Jekyll to turn static text into webpages and preview them locally, while pushing our project changes to GitHub, where they are created into actual webpages by GitHub Pages. We were provided with a stock template on which to start building our page, so we didn't actually build the page from scratch. My experience with Jekyll and GitHub Pages was very pleasant, and I think I am going to use them in my future projects as well. Jekyll seems like a tool which has a lot to offer in terms of webpage development. It also gave me a chance to see how the world of HTML works, which has always seemed kind of scary and complex to me.  
  

Here you can see my local repository, where my webpage contents are located and generated:  

![ ](/assets/img/jekyll.png)  
  
And using the command  

```
bundle exec jekyll serve  
```  

Jekyll builds the webpage and creates a local address for it, from which it can be previewed from before pushing changes to GitHub Pages.   
  
Here you can see what's happening in my terminal when Jekyll is running. Jekyll can be left running in the background and it keeps track of changes to the files in the repository and makes updates real-time.  
  
>       Source: /Users/leo/Documents/HY/cmdline_course/final/leoeer.github.io
       Destination: /Users/leo/Documents/HY/cmdline_course/final/leoeer.github.io/_site
 Incremental build: disabled. Enable with --incremental
      Generating... 
                    done in 0.202 seconds.
 Auto-regeneration: enabled for '/Users/leo/Documents/HY/cmdline_course/final/leoeer.github.io'
    Server address: http://127.0.0.1:4000
  Server running... press ctrl-c to stop.
      Regenerating: 1 file(s) changed at 2018-12-19 16:05:31
                    cmdline-course.md
                    ...done in 0.105715 seconds.

[secret link](/heh.html)



[guten]: https://www.gutenberg.org/
[bee]: http://www.gutenberg.org/ebooks/4511



  


