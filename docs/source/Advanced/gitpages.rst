发布网站到GitHub 
================


什么是 GitHub Pages
----------------------



为你的工程库制作网站 
------------------------------

本节讲述如何为自己的工程制作主页, 并附加API手册项目手册到网站, 以一个例子说明 [#f1]_. 新建一个文件夹, 比如 ``pyml``, 在该文件夹下存放你的工程源码和构建的文档, 以 ``pyml`` 为例, 新建 `pyml` 和 `pyml-docs` 文件夹分别用于存放项目和文档源码和用于发布的网站文件. 


0. 进入 `pyml-docs` 文件夹, 克隆你的库到该文件夹(如 ``git clone https://github.com/antsfamily/pyml.git html``)
   
2. 进入 `html` 文件夹, 此时该包依然为 ``master`` 分支, 使用如下命令为其创建一个 ``gh-pages`` 分支
   
   ::

      git branch gh-pages
      git symbolic-ref HEAD refs/heads/gh-pages  # auto-switches branches to gh-pages
      rm .git/index
      git clean -fdx
      git branch
      
2. 参考 :ref:`_ChapterMakeManualAPI` 小结生成 API文档, 注意修改 `Makefile` 文件中的 输出文件夹路径 ``BUILDDIR`` 为上述 ``html`` 文件夹所在路径, 如果没有修改就手动将生成的 build/html 文件夹中的内容拷贝到 ``pyml-docs/html`` 文件夹下即可.
   
3. 发布网站到GitHub: 执行更改提交即可
   
   ::
   
      git add -A
      git commit "update docs"
      git push origin gh-pages

4. 设置GitHub Pages: 浏览器登录你的 GitHub 账户, 找到你的库 (如 ``pyml`` ), 点击 ``settings --> GitHub Pages --> Source`` 选择 ``gh-pages branch`` 即可
   
5. 访问你的网站: 默认的网址为 ``http://username.github.io/repositoryname``, 你可以自定义域名, 比如本人的将 ``username.github.io`` 换为 ``iridescent.ink`` , 不过你需要买个域名.


目录树结构如下

::

   └── pyml
       ├── pyml
       │   ├── docs
       │   │   ├── make.bat
       │   │   ├── Makefile
       │   │   └── source
       │   │       ├── conf.py
       │   │       ├── index.rst
       │   │       ├── modules.rst
       │   │       ├── pyml.math.rst
       │   │       ├── pyml.nn.rst
       │   │       ├── pyml.rst
       │   │       ├── _static
       │   │       └── _templates
       │   ├── LICENSE
       │   ├── pyml
       │   │   ├── __init__.py
       │   │   ├── math
       │   │   │   ├── geometry
       │   │   │   │   └── generate.py
       │   │   │   ├── __init__.py
       │   │   │   ├── __pycache__
       │   │   │   │   ├── __init__.cpython-36.pyc
       │   │   │   │   └── rand.cpython-36.pyc
       │   │   │   └── rand.py
       │   │   ├── nn
       │   │   │   ├── activations.py
       │   │   │   ├── __init__.py
       │   │   │   └── __pycache__
       │   │   │       ├── activations.cpython-36.pyc
       │   │   │       └── __init__.cpython-36.pyc
       │   │   └── __pycache__
       │   │       └── __init__.cpython-36.pyc
       │   └── README.md
       └── pyml-docs
           └── pyml
               ├── genindex.html
               ├── index.html
               ├── ...
               .
               .
               .






.. rubric:: Footnotes

.. [#f1] http://iridescent.ink/pyml/





