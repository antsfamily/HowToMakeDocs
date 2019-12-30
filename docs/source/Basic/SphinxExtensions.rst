.. _SphinxExtensionDirectives:

Sphinx重要扩展介绍
=======================

Sphinx内置扩展
------------------------

可以通过以下链接找到 Sphinx的扩展:

- `sphinx extensions doc <http://www.sphinx-doc.org/en/master/usage/extensions/index.html>`_  : 官方文档介绍, 含 **Built-in extensions** 和 **Third-party extensions**
- `Awesome Sphinx <https://github.com/yoloseem/awesome-sphinxdoc>`_ : A curated list of awesome tools for Sphinx Python Documentation Generator.
- `sphinx-contrib <https://bitbucket.org/birkenfeld/sphinx-contrib>`_ : a collection of Sphinx extensions maintained by their respective authors. It is not an official part of Sphinx.
- `Survey of Sphinx extensions <https://sphinxext-survey.readthedocs.io/en/latest/>`_ : This is list of Sphinx extensions at October, 2014.


重要内置扩展介绍
~~~~~~~~~~~~~~~~~~~~~~~


目录树 (toctree)
^^^^^^^^^^^^^^^^^^^^^^^^^^

由于 reST 没有处理多个文档, 或将文档分割成多个输出文件的机制, Sphinx使用一个自定义指令来添加组成整篇文档的单个文件间的关系, 以及目录. 这个指令的核心就是 ``toctree`` .

.. tip:: 简单包含某个文件, 可以使用 `include <http://docutils.sourceforge.net/docs/ref/rst/directives.html#include>`_ 指令.


代码与语法着色
^^^^^^^^^^^^^^^^^^^^^^^^^^

更多功能, 参考 `Showing code examples <http://www.sphinx-doc.org/en/stable/usage/restructuredtext/directives.html#showing-code-examples>`_

::

   .. code-block:: python
      :lineno-start: 10
      :emphasize-lines: 9
      :linenos:
      :caption: demo_python.py
      :name: code-PythonGenerateEllipse

      import pytool
      import numpy as np
      import matplotlib.pyplot as plt

      # =====================generate Ellipse=====================
      a = 6  # major axis
      b = 2  # minor axis
      x0 = 10  # center x0
      y0 = 10  # center y0
      N = 1000  # number of points

      # angle for rotating ellipse data
      theta = np.pi * 30 / 180

      x, y = pytool.ellipse_surface(a, b, x0, y0, N, 'rand')

      x = x - np.mean(x)
      y = y - np.mean(y)


   并可以通过 :code-block:numref:`code-PythonGenerateEllipse` 引用代码段.


将被渲染成



.. code-block:: python
    :lineno-start: 10
    :emphasize-lines: 9
    :linenos:
    :caption: demo_python.py
    :name: code-PythonGenerateEllipse

    import pytool
    import numpy as np
    import matplotlib.pyplot as plt

    # =====================generate Ellipse=====================
    a = 6  # major axis
    b = 2  # minor axis
    x0 = 10  # center x0
    y0 = 10  # center y0
    N = 1000  # number of points

    # angle for rotating ellipse data
    theta = np.pi * 30 / 180

    x, y = pytool.ellipse_surface(a, b, x0, y0, N, 'rand')

    x = x - np.mean(x)
    y = y - np.mean(y)


并可以通过 :code-block:numref:`code-PythonGenerateEllipse` 引用代码段.


公式, 图, 表, 代码段编号及引用
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

在 `conf.py` 文件中配置相关选项, 设置是否启用图表公式编号, 以及编号目录深度即格式, 代码如下::

    math_number_all = True  # Set this option to True if you want all displayed math to be numbered. The default is False.
    math_eqref_format = 'Eq.{number}'  # gets rendered as, for example, Eq.10.

    # If True, displayed math equations are numbered across pages when numfig
    # is enabled. The numfig_secnum_depth setting is respected. The eq, not
    # numref, role must be used to reference equation numbers. Default is
    # True.
    math_numfig = True

    # see http://www.sphinx-doc.org/en/master/usage/configuration.html#confval-numfig
    # If true, figures, tables and code-blocks are automatically numbered if they have a caption.
    # The numref role is enabled. Obeyed so far only by HTML and LaTeX builders. Default is False.
    # The LaTeX builder always assigns numbers whether this option is enabled or not.
    numfig = True
    numfig_secnum_depth = 2

    # A dictionary mapping 'figure', 'table', 'code-block' and 'section' to strings that are used for format of figure numbers.
    # As a special character, %s will be replaced to figure number.
    # Default is to use 'Fig. %s' for 'figure', 'Table %s' for 'table', 'Listing %s' for 'code-block' and 'Section' for 'section'.
    numfig_format = {
        'figure': 'Fig. %s',
        'table': 'Table %s',
        'code-block': 'Listing %s',
        'section': 'Section %s',
    }

    numfig_format = {
        'figure': '图 %s',
        'table': '表 %s',
        'code-block': '代码 %s',
        'section': '节 %s',
    }


公式示例, 代码::

  .. math:: e^{i\pi} + 1 = 0
     :label: euler

  使用``label``, 公式将被编号, 可以使用 ``:eq:`euler``` (等效于 :math:numref:`euler` ) 来引用公式 :eq:`euler`.

将被渲染为

.. math:: e^{i\pi} + 1 = 0
   :label: euler

使用``label``, 公式将被编号, 可以使用 ``:eq:`euler``` (等效于 :math:numref:`euler` ) 来引用公式 :eq:`euler`.


图像示例, 代码::

  .. _fig-DeepLearningPlatforms:

  .. figure:: ../_static/figs/mkdocs/demo_reffig.png
     :alt: 深度学习平台
     :align: center

  通过 :figure:numref:`fig-DeepLearningPlatforms` 可以引用.


被渲染为

.. _fig-DeepLearningPlatforms:

.. figure:: ../_static/figs/mkdocs/demo_reffig.png
   :alt: 深度学习平台
   :align: center

通过 :figure:numref:`fig-DeepLearningPlatforms` 可以引用.


表格示例, 代码::

   .. table:: Truth table for "not"
      :name: table-Not

      =====  =====
      A      not A
      =====  =====
      False  True
      True   False
      =====  =====

   可以通过 :table:numref:`table-Not` 引用.

被渲染为

.. table:: Truth table for "not"
   :name: table-Not

   =====  =====
   A      not A
   =====  =====
   False  True
   True   False
   =====  =====

可以通过 :table:numref:`table-Not` 引用.


其它标记指令
~~~~~~~~~~~~~~~~~


下表 给出了语义标记, 详见 `Sphinx Roles <http://www.sphinx-doc.org/en/master/usage/restructuredtext/roles.html#roles>`_.


+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 标记名                       | 示例代码                                                 | 渲染结果                                        | 说明                                                                                                                                      |
+==============================+==========================================================+=================================================+===========================================================================================================================================+
| 缩写 ``abbr``                | ``:abbr:`LIFO (last-in, first-out)```                    | :abbr:`LIFO (last-in, first-out)`               | An abbreviation                                                                                                                           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 命令 ``command``             | ``:command:`ls```                                        | :command:`ls`                                   | The name of an OS-level command                                                                                                           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 下载 ``download``            | ``:download:`this example script <../example.py>```      | :download:`this example script <../example.py>` | This role lets you link to files within your source tree that are not reST documents that can be viewed, but files that can be downloaded |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 文档 ``doc``                 | ``:doc:`Monty Python members </people>```                | :doc:`Monty Python members </people>`           | Link to the specified document; the document name can be specified in absolute or relative fashion                                        |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 编号引用 ``numref``          | ``:numref:`Monty Python members </people>```             | :doc:`Monty Python members </people>`           | Link to the specified figures, tables, code-blocks and sections; the standard reST labels are used.                                       |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 环境变量 ``envvar``          | ``:envvar:`PATH```                                       | :envvar:`PATH`                                  | An environment variable. Index entries are generated. Also generates a link to the matching envvar directive, if it exists.               |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 语法标记 ``token``           | ``:token:`math```                                        | :token:`math`                                   | The name of a grammar token (used to create links between productionlist directives).                                                     |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| Python中的关键字 ``keyword`` | ``:keyword:`ls```                                        | :keyword:`print`                                | The name of a keyword in Python. This creates a link to a reference label with that name, if it exists.                                   |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 选项 ``option``              | ``:option:`-o```                                         | :option:`-o`                                    | A command-line option to an executable program. This generates a link to a option directive, if it exists.                                |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 图形化标签 ``guilabel``      | ``:guilabel:`ls```                                       | :guilabel:`&Cancel`                             | button, menu, title...                                                                                                                    |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 按键 ``kbd``                 | ``:kbd:`Control-x Control-f```                           | :kbd:`Control-x Control-f`                      | Mark a sequence of keystrokes                                                                                                             |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 数学 ``math``                | ``:math:`\alpha```                                       | :math:`\alpha`                                  | 数学公式                                                                                                                                  |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 公式引用 ``eq``              | ``:eq:`xxx```                                            | :eq:`euler`                                     | The name of an OS-level command                                                                                                           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 邮件头 ``mailheader``        | ``:mailheader:`Content-Type```                           | :mailheader:`Content-Type`                      | The name of an OS-level command                                                                                                           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| make变量 ``makevar``         | ``:makevar:`make```                                      | :makevar:`make`                                 | The name of a make variable                                                                                                               |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 首页 ``manpage``             | ``:manpage:`ls(1)```                                     | :manpage:`ls(1)`                                | A reference to a Unix manual page including the section                                                                                   |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 菜单选择 ``menuselection``   | ``:menuselection:`Start --> Programs```                  | :menuselection:`Start --> Programs`             | Menu selection                                                                                                                            |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 程序 ``program``             | ``:program:`notepad```                                   | :program:`notepad`                              | The name of an executable program                                                                                                         |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 正则表达式 ``regexp``        | ``:regexp:`/[1-9][0-9]{0,1}/```                          | :regexp:`/[1-9][0-9]{0,1}/`                     | A regular expression. Quotes should not be included.                                                                                      |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 变量渲染 ``samp``            | ``:samp:`print 1+{variable}`:samp:`print 1+{variable}``` | :samp:`print 1+{variable}`                      | A piece of literal text, such as code. Within the contents, you can use curly braces to indicate a “variable” part, as in file.           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| PythonPEP ``pep``            | ``:pep:`number#anchor```                                 | ---                                             | A reference to a Python Enhancement Proposal                                                                                              |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 命令 ``rfc``                 | ``:rfc:`number#anchor```                                 | :rfc:`number#anchor`                            | A reference to an Internet Request for Comments.                                                                                          |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 定义实例 ``dfn``             | ``:dfn:`person=Person()```                               | :dfn:`person=Person()`                          | Mark the defining instance of a term in the text. (No index entries are generated.)                                                       |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 文件或目录 ``file``          | ``:file:`/usr/lib/python2.{x}/site-packages```           | :file:`/usr/lib/python2.{x}/site-packages`      | The name of a file or directory. Within the contents, you can use curly braces to indicate a “variable” part                              |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+
| 新闻组 ``newsgroup``         | ``:newsgroup:`aaa bbb```                                 | :newsgroup:`aaa bbb`                            | The name of a Usenet newsgroup.                                                                                                           |
+------------------------------+----------------------------------------------------------+-------------------------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------+



下面给出了新增的一些替换指令, 详见 `Sphinx Roles Substitutions <http://www.sphinx-doc.org/en/master/usage/restructuredtext/roles.html#substitutions>`_.


- 发布: ``|release|`` 被渲染为 |release|
- 版本: ``|version|`` 被渲染为 |version|
- 日期: ``|today|`` 被渲染为 |today|



More domains
^^^^^^^^^^^^^^^^^^

The sphinx-contrib repository contains more domains available as extensions; currently Ada, CoffeeScript, Erlang, HTTP, Lasso, MATLAB, PHP, and Ruby domains. Also available are domains for Chapel, Common Lisp, dqn, Go, Jinja, Operation, and Scala. Refer to `Sphinx More domains <http://www.sphinx-doc.org/en/master/usage/restructuredtext/domains.html#more-domains>`_.



第三方扩展
---------------------------------

第三方扩展简介及安装
~~~~~~~~~~~~~~~~~~~~~

如下扩展可以通过类似 ``pip install extensions_name`` 的命令安装, 在 `conf.py` 文件中的 ``extensions`` 中加入该扩展, 以下不在赘述.



推荐使用的第三方扩展
~~~~~~~~~~~~~~~~~~~~


.. _SubSubSection_SphinxcontribProof:

sphinxcontrib-proof
^^^^^^^^^^^^^^^^^^^^^

`sphinxcontrib-proof <https://sphinxcontrib-proof.readthedocs.io/en/latest/>`_  提供定理, 定义, 证明等支持. 在 `conf.py` 文件中的 ``extensions`` 中加入该扩展 ( ``sphinxcontrib.proof`` ) .

然后在 `_static` 目录下新建 `proof.css` 和 `proof.js` 两个文件, 加入如下内容, 你可以自己定义其它的样式.

`proof.css` ::

    .proof {
      margin-top: 1em;
      margin-bottom: 1em;
    }

    /* Titles */
    .proof .proof-title {
      background-color: #0000EE;
      border: 1px solid #86989b;
      color: white;
      font-size: 120%;
      }

    /* Content */
    .proof-content {
      border: 1px solid #9fb1b4;
      background-color: #F0F8FF;
      padding: 0.5em 1em;
    }


    /* Toggle proof */
    .proof-type-proof > .proof-title {
        display: block;
        clear: both;
    }

    .proof-type-proof > .proof-title:after {
        content: " ▼";
    }

    .proof-type-proof > .proof-title.open:after {
        content: " ▲";
    }

`proof.js` ::

      $(document).ready(function() {
          $(".proof-type-proof > *").hide();
          $(".proof-type-proof .proof-title").show();
          $(".proof-type-proof .proof-title").click(function() {
              $(this).parent().children().not(".proof-title").toggle(400);
              $(this).parent().children(".proof-title").toggleClass("open");
          })
      });



使用举例::

    .. _righttriangle:

    .. proof:definition:: Right triangle

       A *right triangle* is a triangle in which one angle is a right angle.

    .. _pythagorean:

    .. proof:theorem:: Pythagorean theorem

       In a :ref:`righttriangle`, the square of the hypotenuse is equal to the sum of the squares of the other two sides.

    .. _proof:

    .. proof:proof::

       The proof is left to the reader.

    You can label and reference definition and theorems (e.g. :numref:`theorem {number} <pythagorean>`). You can also reference proofs (see the :ref:`proof of the Pythagorean theorem <proof>`).


代码将被渲染为

.. _righttriangle:

.. proof:definition:: Right triangle

   A *right triangle* is a triangle in which one angle is a right angle.

.. _pythagorean:

.. proof:theorem:: Pythagorean theorem

   In a :ref:`righttriangle`, the square of the hypotenuse is equal to the sum of the squares of the other two sides.

.. _proof:

.. proof:proof::

   The proof is left to the reader.

You can label and reference definition and theorems (e.g. :numref:`theorem {number} <pythagorean>`). You can also reference proofs (see the :ref:`proof of the Pythagorean theorem <proof>`).


图表编号
^^^^^^^^^^^^^^^^^

借用 jterrace 的论文模版 `sphinxtr <http://jterrace.github.io/sphinxtr/>`_ 中的 ``numfig`` 可以实现. 从 `这里 <https://github.com/jterrace/sphinxtr>`_ 下载源码, 将其中的 `sphinxtr` 放到你的文档源码根目录下, 然后 `conf.py` 添加

.. code-block:: python
   :caption: Code Blocks can have captions.
   :linenos:
   :emphasize-lines: 1,20-22

    sys.path.insert(0, os.path.join(os.path.abspath(os.path.dirname(__file__)), 'extensions'))

    extensions = [
      'sphinx.ext.autodoc',
      'sphinx.ext.doctest',
      'sphinx.ext.intersphinx',
      'sphinx.ext.todo',
      'sphinx.ext.coverage',
      # 'sphinx.ext.imgmath',
      # 'sphinx.ext.mathjax',
      'sphinxcontrib.katex',
      'sphinxcontrib.proof',  # https://framagit.org/spalax/sphinxcontrib-proof/
      'sphinxcontrib.bibtex',  # https://sphinxcontrib-bibtex.readthedocs.io/en/latest/
      'sphinxcontrib.seqdiag',  # http://blockdiag.com/en/
      'sphinx.ext.ifconfig',
      # 'sphinx.ext.viewcode',
      # 'sphinx.ext.githubpages',
      # 'rst2pdf.pdfbuilder',
      # 'sphinx.ext.napoleon',
      'numequ',  # https://github.com/jterrace/sphinxtr/tree/master/extensions
      'numfig',  # https://github.com/jterrace/sphinxtr/tree/master/extensions
      'subfig',  # https://github.com/jterrace/sphinxtr/tree/master/extensions
    ]

    math_numfig = True
    number_figures = True
    figure_caption_prefix = 'Figure'


比如, 这里通过如下代码插入图片:

::

  .. _fig-testFigureNumber:

  .. figure:: ../_static/figs/logo.*
      :alt: Test Figure Number
      :width: 30%
      :align: center

      Test Figure Number

代码将被渲染为

.. figure:: ../_static/figs/logo.*
    :alt: Test Figure Number
    :width: 100%
    :align: center

    Test Figure Number


在其它地方可以通过 ``:num:`fig-testFigureNumber``` 引用,  :ref:`fig-testFigureNumber` .



.. hint:: 新的Sphinx已经支持对数学公式, 图, 表, 代码段进行编号及引用, 建议使用.


.. _SubSubSection_SphinxcontribBibtex:

sphinxcontrib-bibtex
^^^^^^^^^^^^^^^^^^^^^

在 Sphinx中可以使用 `BibTex <http://www.bibtex.org/>`_  , 通过 ``pip install sphinxcontrib-bibtex`` 安装扩展, 并在 `conf.py` 中添加该扩展 ``sphinxcontrib.bibtex`` , 官方文档在 `这里 <https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html>`_ .

然后, 新建 `reference.rst` , 加入如下代码:

.. code-block:: rst
   :caption: reference.rst.
   :linenos:
   :emphasize-lines: 3,5

   .. bibliography:: ./refs.bib
       :list: enumerated
       :start: 1

假如 `refs.bib` 文件中的内容如下:

::

    @Proceedings{1993:PatiOMP,
    author={Y. C. {Pati} and R. {Rezaiifar} and P. S. {Krishnaprasad}},
    booktitle={Proceedings of 27th Asilomar Conference on Signals, Systems and Computers},
    title={Orthogonal matching pursuit: recursive function approximation with applications to wavelet decomposition},
    year={1993},
    volume={},
    number={},
    pages={40-44 vol.1},
    doi={10.1109/ACSSC.1993.342465},
    ISSN={1058-6393},
    month={Nov},
  }


  @article{2003JChPh.118.6720W,
     author = {{Wu}, Y. and {Batista}, V.~S.},
      title = "{Matching-pursuit for simulations of quantum processes}",
    journal = {\jcp},
   keywords = {Tunneling traversal time quantum Zeno dynamics, Foundations of quantum mechanics, measurement theory, Fourier analysis, Integral transforms},
       year = 2003,
      month = apr,
     volume = 118,
      pages = {6720-6724},
        doi = {10.1063/1.1560636},
     adsurl = {http://adsabs.harvard.edu/abs/2003JChPh.118.6720W},
    adsnote = {Provided by the SAO/NASA Astrophysics Data System}
  }

可以通过 ``:cite:`1993:PatiOMP` , :cite:`2003JChPh.118.6720W``` 来引用, 即 :cite:`1993:PatiOMP` , :cite:`2003JChPh.118.6720W` . 如果一次性引用多个文献, 可以用逗号分开, 但不要有空格, 比如这样 ``:cite:`1993:PatiOMP,2003JChPh.118.6720W``` 得到 :cite:`1993:PatiOMP,2003JChPh.118.6720W` .

.. hint::
    如果你想自定义参考文献引用格式, 可以通过 ``pip install pybtex`` 安装 `pybtex <https://docs.pybtex.org/api/plugins.html>`_ , 然后参考 `这里 <https://sphinxcontrib-bibtex.readthedocs.io/en/latest/usage.html#custom-formatting-sorting-and-labelling>`_ 或者下面的讲述配置使用.


.. note::
    ``pybtex`` 提示: 安装好 pybtex 后, 若想在你的文档工程中使用, 需要在 `conf.py` 文件中添加该扩展, 即 ``extensions = ['pybtex']`` , 然后你就可以使用了, 在 ``.. bibliography:: ./refs.bib`` 里添加 ``:style: unsrt`` 即可以更改文献引用格式.

    .. code-block:: rst
       :caption: reference.rst.
       :linenos:
       :emphasize-lines: 2

       .. bibliography:: ./refs.bib
          :style: unsrt

    注意, 如果添加 ``list`` 或 ``start`` 等域, 不能正常渲染, 不能跳转!

sphinxcontrib-xxxdiag
^^^^^^^^^^^^^^^^^^^^^

``xxxdiag`` 包含以下几种类型:

- ``blockdiag`` : `blockdiag <http://blockdiag.com/en/blockdiag/index.html>`_
- ``seqdiag`` : `seqdiag <http://blockdiag.com/en/seqdiag/index.html>`_
- ``actdiag`` : `actdiag <http://blockdiag.com/en/actdiag/index.html>`_
- ``nwdiag`` : `nwdiag <http://blockdiag.com/en/nwdiag/index.html>`_


通过 ``pip install sphinxcontrib-xxxdiag`` 安装扩展, 并在 `conf.py` 中添加该扩展 ``sphinxcontrib.xxxdiag`` , 官方文档在 `这里 <http://blockdiag.com/en/>`_ .

举例: 如

原始代码

::

    .. blockdiag::

     blockdiag {
       blockdiag -> generates -> "block-diagrams";
       blockdiag -> is -> "very easy!";

       blockdiag [color = "greenyellow"];
       "block-diagrams" [color = "pink"];
       "very easy!" [color = "orange"];
     }

渲染结果

.. blockdiag::

   blockdiag {
     blockdiag -> generates -> "block-diagrams";
     blockdiag -> is -> "very easy!";

     blockdiag [color = "greenyellow"];
     "block-diagrams" [color = "pink"];
     "very easy!" [color = "orange"];
   }


原始代码

::

  .. seqdiag::

   seqdiag {
     seqdiag -> "sequence-diagrams" [label = "generates"];
     seqdiag --> "is very easy!";
   }

渲染结果

.. seqdiag::

   seqdiag {
     seqdiag -> "sequence-diagrams" [label = "generates"];
     seqdiag --> "is very easy!";
   }


原始代码

::

  .. actdiag::

     actdiag {
       write -> convert -> image

       lane user {
          label = "User"
          write [label = "Writing reST"];
          image [label = "Get diagram IMAGE"];
       }
       lane actdiag {
          convert [label = "Convert reST to Image"];
       }
     }

渲染结果

.. actdiag::

   actdiag {
     write -> convert -> image

     lane user {
        label = "User"
        write [label = "Writing reST"];
        image [label = "Get diagram IMAGE"];
     }
     lane actdiag {
        convert [label = "Convert reST to Image"];
     }
   }

原始代码

::

  .. nwdiag::

     nwdiag {
       network dmz {
           address = "210.x.x.x/24"

           web01 [address = "210.x.x.1"];
           web02 [address = "210.x.x.2"];
       }
       network internal {
           address = "172.x.x.x/24";

           web01 [address = "172.x.x.1"];
           db01;
           app01;
       }
     }

渲染结果

.. nwdiag::

   nwdiag {
     network dmz {
         address = "210.x.x.x/24"

         web01 [address = "210.x.x.1"];
         web02 [address = "210.x.x.2"];
     }
     network internal {
         address = "172.x.x.x/24";

         web01 [address = "172.x.x.1"];
         db01;
         app01;
     }
   }
