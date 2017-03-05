### 1.注册账户以及创建仓库
要想使用github第一步当然是注册github账号了。
之后就可以创建仓库了（免费用户只能建公共仓库），Create a New Repository，填好名称后Create。

### 2.安装git
github是服务端，要想在自己电脑上使用git，我们还需要一个git客户端。
Windows可以选用msysgit，这个只是提供了git的核心功能，而且是基于命令行的。如果想要图形界面的话只要在msysgit的基础上安装TortoiseGit即可。

Linux上直接用包管理器安装git。
    ```bash
    sudo dnf install git
    ```

### 3.配置Git
首先在本地创建ssh key；

    ```bash
    ssh-keygen -t rsa -C "your_email@youremail.com"  
    ```
后面的your_email@youremail.com改为你的邮箱，之后会要求确认路径和输入密码，我们这使用默认的一路回车就行。成功的话会在~/下生成.ssh文件夹，进去，打开id_rsa.pub，复制里面的key。

回到github，进入Account Settings，左边选择SSH Keys，Add SSH Key,title随便填，粘贴key。为了验证是否成功，在git bash下输入：

    ```bash
    $ ssh -T git@github.com  
    ```


如果是第一次的会提示是否continue，输入yes就会看到：You’ve successfully authenticated, but GitHub does not provide shell access 。这就表示已成功连上github。

接下来我们要做的就是把本地仓库传到github上去，在此之前还需要设置username和email，因为github每次commit都会记录他们。

    ```bash
    $ git config --global user.name "your name"  
    $ git config --global user.email "your_email@youremail.com"
    ```

进入要上传的仓库，右键git bash，添加远程地址：

    ```bash
    $ git remote add origin git@github.com:yourName/yourRepo.git  
    ```

后面的yourName和yourRepo表示你再github的用户名和刚才新建的仓库，加完之后进入.git，打开config，这里会多出一个remote “origin”内容，这就是刚才添加的远程地址，也可以直接修改config来配置远程地址。

### 4.提交、上传

接下来在本地仓库里添加一些文件，比如README，

    ```bash
    $ git add README  
    $ git commit -m "first commit"  
    ```

上传到github：

    ```bash
    $ git push -u origin master  
    ```

git push命令会将本地仓库推送到远程服务器。
git pull命令则相反。

修改完代码后，使用git status可以查看文件的差别，使用git add 添加要commit的文件，也可以用git add -i来智能添加文件。之后git commit提交本次修改，git push上传到github。

### 5.gitignore文件

.gitignore顾名思义就是告诉git需要忽略的文件，这是一个很重要并且很实用的文件。一般我们写完代码后会执行编译、调试等操作，这期间会产生很多中间文件和可执行文件，这些都不是代码文件，是不需要git来管理的。我们在git status的时候会看到很多这样的文件，如果用git add -A来添加的话会把他们都加进去，而手动一个个添加的话也太麻烦了。这时我们就需要.gitignore了。比如一般c#的项目我的.gitignore是这样写的：

    ```
    bin  
    *.suo  
    obj  
    ```


bin和obj是编译目录，里面都不是源代码，忽略；suo文件是vs2010的配置文件，不需要。这样你在git status的时候就只会看到源代码文件了，就可以放心的git add -A了。

### 6.tag

我们可以创建一个tag来指向软件开发中的一个关键时期，比如版本号更新的时候可以建一个“v2.0”、“v3.1”之类的标签，这样在以后回顾的时候会比较方便。tag的使用很简单，主要操作有：查看tag、创建tag、验证tag以及共享tag，这些下面的博客中有详细讲解。
