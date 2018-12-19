---
layout: default
---

# What is this Command-Line Course?  
  
Command-Line Course ([KIK-LG218](https://courses.helsinki.fi/fi/kik-lg218/126710126)) is an online course at the University of Helsinki. The idea of the course is to teach students to operate and navigate in the UNIX environment. The course consists of weekly quizzes which go through the basic commands and tasks one should know when working with code, programming, language technology etc.  
Here are some of the topics we have learned about during the course:  

 * navigating the UNIX system
 * basics of file permissions
 * how to process text corpora
 * Regular Expressions
 * text editor usage
 * how to create and run our own scripts
 * customizing the bash environment
 * installing programs from source
 * version control using Git
 * building webpages with GitHub Pages  

You can read more about the topics and my progress on the course below.

![ ](/assets/img/code.jpg)

### Week 1: Introduction to Command-Line Environments  
  
During the first week, we started with the very basics. We learned what text editors can be used for, and how text files and binary files differ. We were introduced to basic UNIX commands like **cat, less, ls, nano, touch, man, mv, cp, wget** and many more. File types were also discussed and we learned e.g. that not all files have a file extension in the Linux system. We also had our first touch with modifying a [_Project Gutenberg_][guten] book using the **nano** text editor.   
  
In my opinion the first week wasn't difficult at all, possibly because I had already gotten a peak at the UNIX world on a previous course. Although I think that this week was really useful and crucial to learning the more advanced things later down the road. I can imagine someone who has never done anything command-line related finding this week particularly useful (and even a little scary maybe). Overall I think Week 1 was a very good introduction to the topic and to the course, with the support of the first lecture where we got a great presentation which explained how computers work in general.  
  
I will be giving an example of some code correlating to the subject of each week. For example, during Week 1 we learned that the following command can be used to create a new file:  
  
> touch FILENAME  
  

  
### Week 2: Navigating a UNIX system  
  
The second week was about learning how different file permissions effect their usage. We also got to extend our understanding about the structure of the UNIX file system and the working principles behind it. **Sudo** command was introduced, and we got to know what it means to do commit changes as the root user. It was demonstrated to us that for example the commands we used in Week 1 (**ls, cp, nano** etc.) are in fact programs working our system, and by using the commands we have learned we actually just tell these programs what to do. We also learned how to change the permissions of files and directories and how to determine who gets to view, edit and execute them. In addition to these subjects, we studied and learned how symbolic links can be created and how they behave.  
  
The most useful command I learned how to use this week was deifinitely **chmod**. **chmod** is used to change the mode of a file with options and permissions. Since permissions are divided into three categories based on:  
  
1. What the user of the file is allowed to do
2. What a member of your group is allowed to do
3. What all others are allowed to do  
  
These are defined using the options 1 = _u_, 2 = _g_ and 3 = _o_. _a_ can be used if we want to give all these groups the same rights. Read, write and execute rights are referred to with the letters **r, w and x**. The following command would give read rights to everyone.  
> **chmod u=r, g=r, o=r myfile**  
or  
> **chmod a=r myfile**  
  
If we want to make no changes to previous rights and only add a read permission for example, we can use _a+r_ instead of _a=r_.  
  
**chmod** can also be used with octal values (e.g. **chmod 777 myfile**). Each number gives permissions to _u, g and o._ These numbers are calculated using the values given to each permission:  
  
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
  
In the beginning of Week 3 we learned to pipe standard output and commands. Piping basically means taking the result of the first command and forwarding the result to the next command. This opened a world of new possibilites to us, since we were no longer prisoners of using single commands like **less** on the command line. Now we could for instance use the command **echo** and pipe the result in to **less**, which gave us freedom to try all sorts of commands without cluttering the command line, which can happen very easily in text processing.   
  
In week 3 we got a taste of actual [NLP](https://en.wikipedia.org/wiki/Natural_language_processing). We started by using the command **grep** to search for words in texts and using **tr** and **sed** to replace words in text. And not just words, we also learned how to convert large text files (such as the [Life of Bee book][bee] in to sentence-per-line format to make text processing easier. We also learned how to generate frequency lists to see the frequency of most used words in a text file. I thought this was a very cool and useful thing.  
  
Week 3 was probably the most frustrating one for me, since I had some trouble with regular expressions. I did learn how to use them for searching things in corpora, but it was always a pain when my answers were not correct in the week's Quiz. For instance, I used the following regular expression to search for instances of the word "queen" in the [Life of Bee book][bee] (**wc -l** is used for counting the number of matching lines):  
> grep -Eo "(\bqueen\b[^\w-])" life_of_bee.sent | wc -l  
> 136  
  


### Week 4: Scripting and UNIX Configuration Files  
  

  





[guten]: https://www.gutenberg.org/
[bee]: http://www.gutenberg.org/ebooks/4511



  


