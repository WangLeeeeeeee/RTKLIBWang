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

