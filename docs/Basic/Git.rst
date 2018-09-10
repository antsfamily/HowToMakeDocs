
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
++++++++

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
+++++++++++++






版本库管理
+++++++++++



远程仓库
+++++++++


分支管理
+++++++++

标签话管理
+++++++++++


自定义Git
++++++++++


