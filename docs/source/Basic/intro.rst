
文档制作简介
============

该手册采用 `reStructuredText <http://docutils.sourceforge.net/rst.html>`_ 标记语言（ :term:`Markup Language` ）撰写, 使用 `Sphinx <http://www.sphinx-doc.org/en/stable/>`_ 进行发布.


标记语言简介
------------

你可能觉得标记语言是个新名词, 然而你大错特错, 如果我说 `HTML <https://zh.wikipedia.org/wiki/HTML>`_ 、`Latex <https://zh.wikipedia.org/wiki/LaTeX>`_ 也是标记语言, 前者用于创建网页, 后者用于排版文档书籍, 你可能就知道一点了.

简而言之, 标记语言就是特定的标记符号集合, 每个特定标记符可以实现特定的功能（自己总结的）, 如倾斜、加粗、连接、引用等等, 如在reStructureText或者Markdown中, 使用星号括住文本, 可将文本渲染成斜体或粗体, 即 ``*我变斜了*`` 被渲染成 *我变斜了*, ``**我变粗了**`` 被渲染成 **我变粗了** .

Markdown标记语言
++++++++++++++++

`Markdown <https://zh.wikipedia.org/wiki/Markdown>`_ 的 **设计哲学是易读（easy-to-read）易写（easy-to-write）, 是一种轻量级标记语言**, 之所以称为轻量级是因为其标记符号集合较小, 容易记住和使用. Markdown标记语言, 如今被越来越多的写作爱好者和撰稿者广泛使用, 也被大多数现代网站所采用, 如 `GitHub <https://github.com/>`_ 、 `StackOverflow <http://stackoverflow.com/>`_ 、 `简书 <http://www.jianshu.com/>`_ 、 `CSDN <http://www.csdn.net/>`_ 、 `有道云笔记 <http://note.youdao.com/>`_ 、 `Gitblog <http://www.gitblog.cn/>`_ 等等. 此外, 很多开源项目的自述文件 ``README.md`` 就是采用Markdown语言编写的.

Markdown的语法手册可以参见：

- `Markdown——入门指南 <http://www.jianshu.com/p/1e402922ee32/>`_
- `Markdown中文语法指南 <http://www.markdown.cn/>`_
- `创始人John Gruber的Markdown语法说明 <http://daringfireball.net/projects/markdown/>`_

由于Markdown的语法简单, 使得其共功能有限, 因而有了基于Markdown的各种语法扩展, 这里就不再细说, 有兴趣地话自行了解.


reStructuredText标记语言
++++++++++++++++++++++++

`reStructuredText <http://docutils.sourceforge.net/rst.html>`_ 是比Markdown功能更为强大但语法也更为复杂的一种标记语言. 配合Sphinx使用, 可以撰写渲染排版出优美的文档, 且输出格式丰富. 两者的介绍分别见： :ref:`reStructuredTextSimpleTutorial` 和 :ref:`ChaSphinxSimpleTutorial` .


标记语言的优点
++++++++++++++

标记语言的撰写很简单, 不需要很高大上的IDE, 只需要一个能够编辑文字的文本编辑器即可, 完全可以只用Windows系统的“记事本”或者Linux上的“vi”来完成撰写. 这样的类似代码的语言, 很容易使用诸如Git这样的版本控制系统进行管理！可以总结出以下优点：

- 专注于文本内容而不是排版样式
- 兼容所有文本编辑器与字处理软件
- 渲染导出格式丰富, 如HTML、PDF, 借助一些工具还可以导出Latex、epub等文件
- 可以使用Git等版本控制系统管理文章版本
- 可读、直观、易学



使用标记语言需要会什么？
------------------------

- 哈哈, 首先得知道写什么
- 嘿嘿, 你得会打字
- 正经的, 你必须学习一门标记语言的语法（如Markdown、reStructureText）
- 工具1：你需要一个文本编辑器（notepad、vi、**Sublime Text**）
- 工具2：你需要一个该标记语言的解释渲染器（太多了, 不同平台不一样, 如Sphinx）


让我们开始吧！！！
