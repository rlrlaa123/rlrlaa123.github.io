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
1. Make Respository on Github
   * By doing this, you are creating your own space on Github's server.
2. Create new directory that you want to share files with your Repository.
   * On your computer
3. In that directory, start git
   * command is **_git init_**
4. Create Readme.md file
   * **_touch Readme.md_**
   * you created Readme.md file on your computer but you should also upload it on your Repository so that you can share it with your team.
5. Track Readme.md file
   * **_add Readme.md_** or **_add * _** (asterick '*' means everything)
   * By doing so you are telling git to use or point at such file.
6. Check what the git is pointing or about to do.
   * **_git status_**
   * This command will show what kind of changes it will perform.
7. Commit the change
   * **_git commit -m "write_message"_**
   * Commit means you are performing the change. Think of all the open-source projects on Github, whenver people make changes to the code, they are committing to the project. I think this is why Git calls it commit.
8. Add remote repository
   * **_git remote add [repository_name] [repository_address]_**
   * You should tell the git where the repository you made on Github is and add the direction on your computer.
9. Check your remote repository
   * **_git remote_**
10. Upload the committed changes to your repository
   * **_git push -u [repository_name] [branch_name]_**
These steps can be followed when you first made your repository.
