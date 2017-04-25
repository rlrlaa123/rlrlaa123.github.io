---
title: Reading Linux Bible
subtitle: Creating Shell Environment
image: http://image3.kangcom.com/2016/09/b_pic/201608262585.jpg
---
###### Friend borrowed me a book 'Linux Bible'. Front part was so boring, discussing about history of linux. It was interesting and boring at the same time. Reason it was interesting is because it is the stories that people around me would be interested, but for me, it doesn't really interest me that much...(I wish it was!)
![book](http://image3.kangcom.com/2016/09/b_pic/201608262585.jpg)

###### Today, I was struggling with setting path to spark for my shell. So, creating shell environment part for this book was quite interesting and it is the thing I'd like to remember.

### Creating Shell Environment
It is one method to increase efficiency of task by tuning shell. By adding environment path, everytime you open shell, added variables can be used. 
For exmaple, if you add JAVA_HOME environment, in shell if you write 'java' it will automatically lead you to java directory and execute java.

There are several files for setting bash...(I'm using zsh, so mine is different! ex..zshrc)
* ~/.bash_profile 
    * Each user's information are set. 
    * This file is applied once when user login, sets basic env variables, also apply user's .bashrc file's setting.
    * Mother of ./bashrc
* ~/.bashrc 
    * It is only limited to user's bash shell. It is applied when login, and when new bash shell is opened. Therefore, perfect place to set alias.
    * It is where we usually set path when downloaded new program.
* ~/. bash_logout
    * Set when you logout(turn off shell). Basic function is to clean the screen.

### Adding Enviroment Variable
These environment variables are added to .bashrc file.

* TMOUT
    * Sets idle time until bash is off. It is in second, it is the longest time that shell can stay without any input. It is somewhat similar to screensaver. (You should make it long enough so that it doesn't quit while still working!)
* PATH
    * It sets where the user will find for input direction. If you want to add /getstuff/bin/ directory, you should do this,
    ```linux
    PATH=$PATH:/getstuff/bin ; export PATH
    ```
    If you do this, it will call current PATH($PATH), and add /getstuff/bin/ directory, send new PATH.
* EVERYTHING
    * This literally means everything, it's not how it is called, you can make any path to be environment variable. For example, if you downloaded spark, you should set SPARK_HOME path and add it to bashrc file so that it can be used in any directory in shell.
