
.. _ChaVersCtrlGit:

版本控制系统Git教程
===================

**什么是版本控制系统 (Version Control System)?** `版本` 这一词大家都不陌生, 那么想必也能猜出来版本控制系统的含义: 能够自动管理文件版本的系统. 这句话似乎是废话, 举个例子来说, 平时在写文章或代码时, 经常会复制多个文件以保存不同版本的修改, 而且你还的重命名文件, 以告诉自己这一版本在哪里修改了, 是不是很繁琐, 不仅如此, 你还要存储不同的文件版本, 那么版本控制系统就是帮你完成这件事, 比如, 它可能会像下面这样自动记录每个版本的变动:

+------+------+------------------------+------------+
| 版本 | 用户 | 说明                   | 日期       |
+======+======+========================+============+
| 1    | 张三 | 删除了软件服务条款5    | 7/12 10:38 |
+------+------+------------------------+------------+
| 2    | 张三 | 增加了License人数限制  | 7/12 18:09 |
+------+------+------------------------+------------+
| 3    | 李四 | 财务部门调整了合同金额 | 7/13 9:51  |
+------+------+------------------------+------------+
| 4    | 王五 | 延长了免费升级周期     | 7/14 15:17 |
+------+------+------------------------+------------+


你可能还希望恢复不同的版本状态时的文件, 可以的, 就是说你有后悔药可以吃的. 怎么样? 是不是突然觉得自己要解放了, 不过你得先学会使用一款版本控制系统软件才行. 下面开始吧!!!


此教程部分内容参考了 `Git教程 - 廖雪峰的官方网站 <http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000>`_ 号称最浅显易懂的教程, 是吗? 是的, 至少我觉得是.


What is Git?
-------------



   Git is a free and open source distributed version control system designed to handle everything from small to very large projects with speed and efficiency.


Git (读音/gɪt/) 是一个免费开源的分布式版本系统, 无论项目大小, 都能游刃有余地管理项目的版本. 我们还希望它是易学的, 是的, 它也确实如此! 右图为 Git 的 logo.

.. figure:: ../_static/figs/mkdocs/git_logo.png
   :alt: Logo of Git
   :scale: 40%
   :align: right

   Logo of Git




**Git 与 GitHub**: 我们知道 Git 是一个免费开源的分布式版本系统, 跟svn、cvs是同级的概念, 那么 `GitHub <https://github.com/>`_ 是什么呢? 是一个免费的远程仓库, 顾名思义就是用来存储你的文件的, 给用户提供git服务. 这样你就不用自己部署git系统, 直接用注册个账号, 用他们提供的git服务就可以. 右图为其吉祥物 Octocat .


.. figure:: ../_static/figs/mkdocs/github_logo.png
   :alt: Logo of Github
   :scale: 40%
   :align: right

   Github 吉祥物 Octocat


Why Git?
---------

- 免费开源
- 分布式
- 高效高速
- 简单易学




How to
-------

下面给出一些学习参考资料:

- `Git教程 - 廖雪峰的官方网站 <http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000>`_ 自称最浅显易懂的Git教程.

- `Pro Git <https://git-scm.com/book/en/v2>`_ : 由 Scott Chacon and Ben Straub 写的一本书, 可以在线浏览, 也可以下载 PDF, epub, mobi, html 版本查看, 被翻译成多种语言, 简体中文版在 `这里 <https://git-scm.com/book/zh/v2>`_ 查看与下载.



安装Git
~~~~~~~~~~~~

Windows
^^^^^^^^

可以从 `Git 官网 <https://git-scm.com/>`_ 下载 Windows 版 Git 安装包 https://git-scm.com/download/win , 根据提示安装即可.

此外, `Git for Windows` 是一个轻量级且具有 `Git SCM <http://git-scm.com/>`_ 全特性的 Git 软件 , 可以从 https://git-for-windows.github.io 下载安装.

   Git for Windows focuses on offering a lightweight, native set of tools that bring the full feature set of the Git SCM to Windows while providing appropriate user interfaces for experienced Git users and novices alike.


Linux
^^^^^^

Git 在 ubuntu 上的安装很简单, 首先终端 ( 快捷键 ``Ctrl + Alt + T`` ) 输入 ``git`` , 查看是否已安装, 如果没有, 对于 Ubuntu 系统通过如下命令安装即可: ::

   sudo apt-get install git

其它系统可以根据 `Git官网 <https://git-scm.com/>`_ 提示下载安装.




创建本地仓库
~~~~~~~~~~~~~~~~






版本库管理
~~~~~~~~~~~~


瘦身
^^^^^^^^^^^^^^^^

对于一个git库, 提交次数多了, 特别是库中含有大文件时, 会使得库显得很臃肿, 如果直接删除 `.git` 文件夹会带来很多问题, 使用下面的命令可以清空提交历史缓存, 保持最新代码, 达到瘦身的效果.

.. code-block:: bash

    # 1. Checkout

    git checkout --orphan latest_branch

    # 2. Add all the files

    git add -A

    # 3. Commit the changes

    git commit -am "commit message"

    # 4. Delete the branch

    git branch -D master

    # 5. Rename the current branch to master

    git branch -m master

    # 6. Finally, force update your repository

    git push -f origin master




远程仓库
~~~~~~~~~~~~~~~~

分支管理
~~~~~~~~~~~~~~~~
标签话管理
~~~~~~~~~~~~~~~~

Git命令概览
------------

.. code:: bash

    初始化操作
        $ git config --global user.name <name> #设置提交者名字
        $ git config --global user.email <email> #设置提交者邮箱
        $ git config --global core.editor <editor> #设置默认文本编辑器
        $ git config --global merge.tool <tool> #设置解决合并冲突时差异分析工具
        $ git config -list #检查已有的配置信息
    创建新版本库
        $ git clone <url> #克隆远程版本库
        $ git init #初始化本地版本库
    修改和提交
        $ git add . #添加所有改动过的文件
        $ git add <file> #添加指定的文件
        $ git mv <old> <new> #文件重命名
        $ git rm <file> #删除文件
        $ git rm -cached <file> #停止跟踪文件但不删除
        $ git commit -m <file> #提交指定文件
        $ git commit -m “commit message” #提交所有更新过的文件
        $ git commit -amend #修改最后一次提交
        $ git commit -C HEAD -a -amend #增补提交（不会产生新的提交历史纪录）
    查看提交历史
        $ git log #查看提交历史
        $ git log -p <file> #查看指定文件的提交历史
        $ git blame <file> #以列表方式查看指定文件的提交历史
        $ gitk #查看当前分支历史纪录
        $ gitk <branch> #查看某分支历史纪录
        $ gitk --all #查看所有分支历史纪录
        $ git branch -v #每个分支最后的提交
        $ git status #查看当前状态
        $ git diff #查看变更内容
    撤消操作
        $ git reset -hard HEAD #撤消工作目录中所有未提交文件的修改内容
        $ git checkout HEAD <file1> <file2> #撤消指定的未提交文件的修改内容
        $ git checkout HEAD. #撤消所有文件
        $ git revert <commit> #撤消指定的提交
    分支与标签
        $ git branch #显示所有本地分支
        $ git checkout <branch/tagname> #切换到指定分支或标签
        $ git branch <new-branch> #创建新分支
        $ git branch -d <branch> #删除本地分支
        $ git tag #列出所有本地标签
        $ git tag <tagname> #基于最新提交创建标签
        $ git tag -d <tagname> #删除标签
    合并与衍合
        $ git merge <branch> #合并指定分支到当前分支
        $ git rebase <branch> #衍合指定分支到当前分支
    远程操作
        $ git remote -v #查看远程版本库信息
        $ git remote show <remote> #查看指定远程版本库信息
        $ git remote add <remote> <url> #添加远程版本库
        $ git fetch <remote> #从远程库获取代码
        $ git pull <remote> <branch> #下载代码及快速合并
        $ git push <remote> <branch> #上传代码及快速合并
        $ git push <remote> : <branch>/<tagname> #删除远程分支或标签
        $ git push -tags #上传所有标签

自定义快捷命令
~~~~~~~~~~~~~~

.. code:: bash

    alias gcommit='func() { git commit -m $1;}; func'
    alias gpush='git push -u origin master'
    alias gadd='git add -A'

.. code:: bash

    # for my git server
    alias gitclone='func() { git clone git@lab.ink:/home/git/repositories/$1;}; func'
    #alias gitclone='func() { git clone git@$LABIP:/home/git/repositories/$1;}; func'
    alias gitadd='func() { sudo /home/liu/sfw/zhi/gitadd.sh $1;}; func'
    alias upd='func() { sudo /home/liu/sfw/zhi/updatedomain.sh $1;}; func'


    # for git
    alias gcommit='git commit -m'
    alias gpush='func() { git push -u origin $1;}; func'
    alias gpushm='git push -u origin master'
    alias gpushp='git push -u origin gh-pages'
    alias gadd='git add -A'
    alias gstatus='git status'

子模块
------

自动下载
~~~~~~~~

如果你在克隆含有子模块的库时， 没有使用 ``git clone --recursive xxx`` ，
那么不要急， 可以这样把子模块克隆进去

.. code:: bash

    cd [project]
    git submodule init
    git submodule update

搭建Git服务器
----------------

参考示例
~~~~~~~~~~~~~~

-  `Git本地服务器搭建及使用详解 <https://www.cnblogs.com/linsanshu/p/5512038.html>`__
-  `搭建Git服务器 <https://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/00137583770360579bc4b458f044ce7afed3df579123eca000>`__
-  `在服务器上部署
   Git <https://gitee.com/progit/4-%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E7%9A%84-Git.html#4.2-%E5%9C%A8%E6%9C%8D%E5%8A%A1%E5%99%A8%E4%B8%8A%E9%83%A8%E7%BD%B2-Git>`__

安装配置SSH服务端客户端
~~~~~~~~~~~~~~~~~~~~~~~~~~~

1. 安装SSH: ``sudo apt-get install openssh-server openssh-client``
2. 配置SSH服务端(可选, 默认配置下需要输入密码)：
   ``sudo gedit /etc/ssh/sshd_config`` --> ``StrictModes  no`` ,
   ``RSAAuthentication yes`` (使用纯的RSA认证),
   ``PubkeyAuthentication yes`` (允许Public Key) ,
   ``AuthorizedKeysFile     %h/.ssh/authorized_keys`` (公钥存储路径).
3. 重启SSH服务: ``sudo /etc/init.d/ssh restart`` 或
   ``sudo service ssh restart``

安装配置Git服务端客户端
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Git服务端配置
^^^^^^^^^^^^^^^^^

1. 安装服务端: ``sudo apt-get install git git-core``
2. 新建用户用于git : ``sudo adduser git`` (或 ``sudo useradd -m git`` ，
   ``sudo passwd git``)
3. 将git设为管理员(可选): ``sudo gedit /etc/sudoers`` --> 添加
   ``git ALL=(ALL:ALL)  ALL``
4. 新建仓库目录并更改权限

   .. code:: bash

      cd /home/git
      sudo mkdir repositories
      sudo chown git:git /home/git/repositories # 设定所有者
      sudo chmod 755 /home/git/repositories # 设置仓库访问权限
      cd repositories
      sudo git init --bare sample.git # 创建 sample 库
      sudo chown -R git:git sample.git # 更改 sample 权限


**提示:**

出于安全考虑，可以限制git用户通过ssh使用git，但无法登录shell。 打开编辑
``/etc/passwd`` 文件并找到 类似 下面的一行(自行创建的用户名)：

``git:x:1001:1001:,,,:/home/git:/bin/bash``

改为：

``git:x:1001:1001:,,,:/home/git:/usr/bin/git-shell``

Git客户端配置
^^^^^^^^^^^^^^^^^


1. 安装Git客户端（Windows，或Linux）
2. 生成免密登录的秘钥（可选）: 打开 ``gitbash`` (Windows) 或终端
   (linux)， 输入以下指令生成秘钥

``bash    ssh-keygen -t rsa`` 生成的秘钥一般在
``C:/Users/yourname/.ssh/id_rsa.pub`` (Windows), ``~/.ssh/id_rsa.pub``
(Linux) 文件中.

3. 秘钥上传到服务器: 方法1 --> 在\ ``/home/git/`` 下 新建
   ``.ssh/authorized_keys`` 文件 (如果没有), 复制上述生成的秘钥内容,
   粘贴到 authorized\_keys 中保存. 方法2 --> 客户端gitbash终端执行:
   ``ssh-copy-id git@yourhost``

4. 克隆服务端的仓库:

``bash    git clone git@yourhost:/home/git/repositories/samples.git``

5. 提交到服务端:

``bash    git push -u orig master``

按上述步骤配置完即可

简化命令
--------

自定义域名
~~~~~~~~~~

通过修改 ``host`` 文件实现：

-  Windows: ``C:/Windows/System32/drivers/etc/hosts``
-  Ubuntu : ``/etc/hosts``

打开文件，添加域名解析条目即可：

.. code:: bash

    # server at lab
    # IP domain
    xxx.xxx.xxx.xxx lab.ink

克隆
~~~~

采用 ``alias`` 实现命令的简化：

Windows与Linux命令相同, 只不过目录不一样：

-  Linux下在 ``~/.bashrc`` 里
-  Windows下在 ``C:\Users\yourusername/.bashrc`` 里，如果没有，gitbash
   终端执行 : ``touch .bashrc`` 即可

打开该文件，并输入:

.. code:: bash

    alias gitclone='func() { git clone git@lab.ink:/home/git/$1;}; func'

重启终端，以后可以通过执行如下命令进行克隆：

.. code:: bash

    # gitclone your_git_repository_name
    gitclone sample

错误解决
--------

Clone过程
~~~~~~~~~

clone 时提示如下错误

.. code:: bash

    gitclone sample
    Cloning into 'sample'...
    ssh: connect to host lab.ink port 33: Connection timed out
    fatal: Could not read from remote repository.

通过将端口 ``33`` 改为 ``22`` 即可。 ``sudo gedit /etc/ssh/ssh_config``
找到 ``Port`` 修改即可。

**提示：**

-  SSH服务端配置: ``sudo gedit /etc/ssh/sshd_config``
-  SSH客户端配置: ``sudo gedit /etc/ssh/ssh_config``

SSH秘钥
~~~~~~~

明明添加了秘钥，却提示：

.. code:: bash

    sign_and_send_pubkey: signing failed: agent refused operation

解决办法：

.. code:: bash

    eval "$(ssh-agent -s)"
    ssh-add


