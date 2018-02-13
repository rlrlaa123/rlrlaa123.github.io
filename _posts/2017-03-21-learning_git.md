---
layout: post
title: Simple Git Tutorial
subtitle: How to use Git + Repository
image: http://haacked.com/images/icons/Shell.ico
---

###### Before you read my post, you should aware that my understanding of Git is very low if you need deeper knowledge or tutorial about using Git please go back to Google. I learned how to use Git from my friend for one day and writing this to kind of recall myself.

Hello there, I'm going to share what I learned and practiced with Git.
I'd say Git is a teamwork-support software that can track the history of revision of codes and upload and deletetion of files.
I know the explanation of it is too vague so I'll show the example.

Below is the picture of Github commit screen. Github is the web service for managing server-side of Git.

![git_example](/img/git-example.PNG)

So when I upload the file to Github with changed code, it will compare the difference between the previous code(red part) and new code(green part). Do you kind of get the idea?

Straight to the point, this is how I used Git.
### These steps can be followed when you first make your repository.

1. Make Respository on Github
   * By doing this, you are creating your own space on Github's server.
2. Create new directory that you want to share files with your Repository.
   * On your computer
3. In that directory, start git 
        ```
        git init
        ```
    * command is
4. Create Readme.md file 
        ```
        touch Readme.md
        ```
   * you created Readme.md file on your computer but you should also upload it on your Repository so that you can share it with your team.
5. Track Readme.md file 
        ```   
        git add Readme.md
         OR
        git add *
        ```
   * (asterick '*' means everything)
   * By doing so you are telling git to use or point at such file.
6. Check what the git is pointing or about to do. 
        ```   
        git status
        ```
   * This command will show what kind of changes it will perform.
7. Commit the change 
        ```
        git commit -m "write_message"
        ```
   * Commit means you are performing the change. Think of all the open-source projects on Github, whenver people make changes to the code, they are committing to the project. I think this is why Git calls it commit.
8. Add remote repository 
        ``` 
        git remote add [repository_name] [repository_address]
        ```
   * You should tell the git where the repository you made on Github is and add the direction on your computer.
9. Check your remote repository 
        ```
        git remote
        ```
10. Upload the committed changes to your repository 
        ```
        git push -u [repository_name] [branch_name]
        ```
### This is how I clone other repository to mine

1. fork the repository
2. click clone and download button
3. copy url to request HTTP
4. clone it to your local directory 
        ```
        git clone_ [request url]
        ```
5. Track everychange 
        ```
        git add *
        ```
   * check every changes on the directory
6. commit
7. push

### When you change something on your Github repository
Don't forget to do **_git push_** This command will update every changes from your repository to your directory.

Thank you for reading!
