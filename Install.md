# Show markdown file in ubuntu
pandoc file.md | lynx -stdin
# Obtain source code
The official website is: [RTKLib](www.rtklib.com)

clone the souce code:

```
git clone git@github.com:tomojitakasu/RTKLIB.git
```
build the aim software
```
cd app/<you aim app>
cd gcc
make
sudo make install 
```
the most helpful information can be found in RTK manual.

# Git implementation problems
The tutorial can be found here: [Github Implement](www.runoob.com/w3cnote/git-guide.html)

The basic steps are:
1. Sign up a github account, install git on your computer
2. Create ssh key: 
```
ssh-keygen -t rsa -C "you_emial@youremail.com"
```
then you will get ssh file under ~/ directory, note that you may need use "ls -a" to see this directory. Open it and copy the content to your github account sssh key setting box. Use 
```
ssh -T git@github.com
```
to test if successfully connected.

3. Set username and email
```
git config --global usernmae "your name"
git config --global user.email "your_email@youremail.com"
```
4. Add remote server:
```
git remote add origin git@github.com:yourName/yourRepo.git
```
5. Normally you can git pull, push with remote repository, and git init, add ., commit -m "comments" with local buff

## Problems you might encounter
1. Error: when you push "Updates were rejected because the remote contains work that you do" the solution to this is we need to use 
```
git pull origin master 
```
before 
```
git push -u origin master
```
2. Error: when you push "updates were rejected because the tip of your current branch is behind its remote counterpart" the solution to this is the same as 1.

3. Error: when you pull "fatal: refusing to merge unrelated histories", the solution is to add "-allow-unrelated-histories"
```
git pull origin master --allow-unrelated-histories
``` 
and you might see "please enter a commit message to explain why this merge is necessary ...", if it is opened by vim, you can quit by enter :wq, or if it is in nao model, you ocan press ctrl+x to quit.

4. The authenticity of host 'github.com' can't be established: you need to create ssh key in your computer and add to your github account

5. Error: fatal not a git repository (or any of the parent directories) .git
```
git init
```

## How to share folder between virtual machine and host
1. Opening the settings in Oracle VM VirtualBox Manger and set the folder in "Shared Folders"

2. Click Auto-mount and Make Permanent, se the mount point to "/home/wanglee/Documents/share"

3. If yoy do not have the permission, use:
```
chmod 777 share
```
