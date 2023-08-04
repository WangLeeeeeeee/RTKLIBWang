# Obtain source code
The official website is: [RTKLib](www.rtklib.com)

clone the souce code:

```
git clone git@github.com:tomojitakasu/RTKLIB.git
```

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
