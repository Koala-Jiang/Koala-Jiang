# Git Control

learned from https://www.liaoxuefeng.com

## Install Git

Linux: 

> $ sudo apt-get install git
>
> 源码安装：./config + make + sudo make install

 

Win: 

> 下载安装， git bash,
>
> $ git config --global user.name"".
>
> $ git config --global user.email"".



Mac OS X:

> Xcode / Preferences / Downloads / Command Line Tools / Install
>
> homebrew



## Build Repository

找个合适的地方,目录不含中文

$ mkdir cutegit

$ cd cutegit

$ git init

编写keai.txt文档

$ git add keai.txt

$ git commit -m "Ke Ai de Wen Dang"

## Go Back to History

$ git log //record all the versions, commit

$ git log --pretty=oneline //simplified version

//git 版本号是 SHA1算出，16进制的数字

//HEAD 为当前版本， 上一个HEAD^， 上上个 HEAD^^, 前100个 HAED~100

$ git reset --hard HEAD^ // get to last version

$ git reset --hard <version id>

$git reflog //record all the command, useful to return to thrown away version, version id can be found

## Working Directory and Repository

Working directory: 电脑上能看到的目录

Repository： Stage + Master (automatic created by git, with a pointer called HEAD)

$ git status // check out status of Stage

//git add -> add changes to Stage 

//git commit -> commit changes from Stage to Repository 

//rm <FILE_NAME> -> remove file from working directory

//git restore <FILE_NAME>

//git rm <FILE_NAME> -> remove file from repository, remember to commit afterwards

$ git diff HEAD -- <FILE_NAME> //see diffs between working directory and repository

$ cat <FILE_NAME> //see file content

$ git checkout -- <FILE_NAME> // to discard changes in working directory, no matter it's change or delete

$ git reset HEAD <FILE_NAME> // turn changes staged into upstaged

## Github

本地和github通过SSH加密

1. 创建SSH Key, 打开Shell / Win gitbash， $ ssh-keygen -t rsa -C"youremail@hello.com" // user/.ssh/id_rsa+id_rsa.pub私钥和公钥
2. Github / account settings / SSH Keys / Add SSH Key /     copy id.rsa_pub into Key box



添加到远程 （先有本地库）

$ git remote add origin git@github.com:xxx/xxx.git

$ git push -u origin master (first time) $git push origin master

$ git remote -v (see info of remote)

$ git remote rm origin (disconnect relation between local and remote) 

从远程clone （没有本地库）

Create repository in github, create readme.md

$ git clone git@github.com:xxx/xxx.git

$ cd xxx

$ ls (read inside)

## Branche Management

### Basic

#### init

![image-20210522175833349](pics/image-20210522175833349.png)

#### build new branch

> $ git checkout -b dev 
>
> //switched to new branch dev
>
> Equal to 
>
> $ git branch dev //build
>
> $ git checkout dev //enter
>
> Or $ git switch -c <name>
>
> $ git branch //see the branch

<img src="pics/image-20210522175838956.png" alt="image-20210522175838956" style="zoom: 67%;" />

#### merge into master

> $ git merge dev //merge dev into master
>
> $ git branch -d dev //delete branch dev

<img src="pics/image-20210522175910393.png" alt="image-20210522175910393" style="zoom:67%;" />

### Conflict

如果master和feature1 两处都修改了并且commit了，需要解决conflict

手动解决

> $ git status //check out info of branches and conflict
>
> $ git add xxx.xx
>
> $ git commit -m ""
>
> $ git log --graph 可以查看分支合并图



<img src="pics/image-20210522175933135.png" alt="image-20210522175933135" style="zoom:67%;" />