---
title: Linux - File Permission and Ownership
subtitle: ls -ld,chmod,chown,mv,rm
image: https://3c1703fe8d.site.internapcdn.net/newman/gfx/news/hires/2014/linux.jpg
---
###### I mistakenly deleted other person's file with rm command on AWS linux server. While I was trying to download extundelete program and utilize it, I suffered so much with permission problem. So I pick up this 'Linux Bible' book again and studied little bit about such problems. 
---
Before looking at permissions, you need to be aware of this weird format, meaning permissions. -rwxrwxrwx. File permission is consists of 9 bits, whether it can be read, written or executed.
__*-rwxrwxrwx*__ 
1. First 3 bit displays owner's permission
2. Next 3 bit displays group's permission
3. Last 3 bit displays other user or group's permission.

### Looking at permission and ownership
```linux
$ ls -ld Users dev
drwxr-xr-x  5 root  admin   170  4 18 13:40 Users
dr-xr-xr-x  3 root  wheel  5315  4 28 17:43 dev
```
dr means it is a directory. On Users, owner is root and group is admin. Owner can read, write, execute, group can execute and read, other user can only execute this file.
dev directory is similar while it cannot be written with owner.

###### This is how you read permission and ownership

### Chaning permission with *chmod*
You can change permission using chmod. There are two ways of chaning it but we will only look at number way because changing it in letter seems more complicated and either way is the same.
There is number assignd to each permission. (r=4,w=2,x=1)
Their total value will be the permission. For example, 7 is rwx, 4 is r, 1 is x. So, the results will be like these.
```linux
# chmod 777 file
Result is rwxrwxrwx
```
```linux
# chmod 755 file
Result is rwxr-xr-x
```
```linux
chmod 000 file
Result is ---------
```
```linux
In order to assign permission to whole directory, you will do this.
$ chmod -R 755 $HOME/myapps
Result is rwxr-xr-x for myapps directory and all the sub-directroy under it.
```

### Setting file permission with *umask*
When normal user create a file or directory, basic permission is rw-rw-r--. For directory it is, rwxrwxr-x. For root user, permission for file and directory is rw-r--r-- and rwxr-xr-x. Setting this is umask. If you type you can check the current umask.
```linux
$ umask
0002
```
Let's ignore the first 0 for now. This usmask value is considered as total 666 in file and 777 in directory and subtracted from them. So, total-umask. For example, if umask is 002, umask's directory permission is 775(rwxrwxr-x), and file is 664(rx-rx-r--). In order to temporarily change umask value, you will do umask command.
```linux
$ umask 777 ; touch file01 ; mkdir dir01 ; ls -ld file01 dir01
d---------. 2 joe joe 6 Dec 19 11:03 dir01
----------. 1 joe joe 0 Dec 19 11:02 file01
$ umask 000 ; touch file02 ; mkdir dir02 ; ls -ld file02 dir02
drwxrwxrwx. 2 joe joe 6 Dec 19 11:00 dir02/
-rw-rw-rw-. 1 joe joe 0 Dec 19 10:59 file02
$ umask 022 ; touch file03 ; mkdir dir03 ; ls -ld file03 dir03
drwxr-xr-x. 2 joe joe 6 Dec 19 11:07 dir03
-rw-r--r--. 1 joe joe 0 Dec 19 11:07 file03
```
In order to change umask value permanately, you need to add umask command to home directory's .bashrc file.

### Changing file's onwnership with *chown*
Normal user cannot change the ownership of file or directory. Only root user can change ownership.
```linux
# chown joe /home/joe/memo.txt
# ls -l /home/joe/memo.txt
-rw-r--r--. 1 joe root 0 Dec 19 11:23 /home/joe/memo.txt
```
However, only the user's ownership is changed not group. To also change group ownerhips,
```linux
# chown joe:joe /home/joe/memo.txt
# ls -l /home/joe/memo.txt
-rw-r--r--. 1 joe joe 0 Dec 19 11:23 /home/joe/memo.txt
```
chown can also be used to change all the sub-file and directory.
```linux
# chown -R joe:joe /media/myusb
```
This will change ownership of all the materials under them.
* ls -l will show the current directory's all files and directory's permission and ownership.
* ls -l *directory name* will give all files and directroy's permission and ownership under chosen directory.
* ls -ld will show the current directory's permission and ownership.
* ls -ld *directroy name* will only give directroy's permission and ownerhip.

### File move, copy and delete
```linux
$ mv abc def
```
It moves abc file to def directory. 
mv can overwrite to same file or directory.
```linux
$ cp abc def
$ cp -r /usr/shar/doc/bash-completion* /tmp/a/
$ cp -ra /usr/share/doc/bash-completion* /tmp/b/
```
It copies abc file to def directroy. For second command, -r option copies all the materials inside directroy to given path. Third command with added -a option copies data/time stamp and permission. Without -a option copied file will get new data/time stamp.
cp can also overwrite to same file or directory.
```linux
$ rm abc
$ rm *
```
rm will delete abc file and rm * will erase all the files and directroy in the current directory.
```linux
$ rmdir /home/joe/nothing/
$ rm -r /home/joe/bigdir/
$ rm -rf /home/joe/hugedir/
```
rmdir will delete nothing directory. -r option will delete all the files and directroy inside bigdir. -f option will ignore user's permission, forcing it to be deleted.
* __Catuion!!__ : mv,cp,rm can be dangerous as it can overwrite or delete files and directroy and it can cause big accidents. Therefore, -i option alias should be given. So that it asks the user again about deleting the file.
    * So I added alias -i option for each function on my .bashrc file.
    ```linux
    alias mv = 'mv -i'
    alias cp = 'cp -i'
    alias rm = 'rm -i'
    ```
    * If commands will overwrite the file, -i option will ask if it will overwrite the file. Such a safe option! : )
*  However, this can be uncomfortable everytime you delete a file or directory when you are sure.
    * You can use -f option to ignore the -i option. 
    * You can also add / in front of mv,cp,rm and it will ignore the alias.
