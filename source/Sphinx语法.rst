Sphinx语法
==========

子标题
------

子子标题
+++++++

.. attention::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. danger::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. error::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. hint::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. important::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. note::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. tip::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. warning::
      不在于刷了多少题目，一定要理解每一次刷的题目

.. admonition:: 我的语录
    10不在于刷了多少题目，一定要理解每一次刷的题目

列表
----

* This is a bulleted list.
* It has two items, the second
  item uses two lines.

1. This is a numbered list.
2. It has two items too.

#. This is a numbered list.
#. It has two items too.

术语解释
--------

term (up to a line of text)
   Definition of the term, which must be indented

   and can even consist of multiple paragraphs

next term
   Description.

断行
----

| These lines are
| broken exactly like in
| the source file.

代码块
------

This is a normal text paragraph. The next paragraph is a code sample::

   It is not processed in any way, except
   that the indentation is removed.

   It can span multiple lines.

This is a normal text paragraph again.

>>> 1 + 1
2

.. literalinclude:: himmelblau.py
    :language: python
    :caption: Literal includes can also have captions.
    :linenos:
    :lines: 1-40



def my_function(my_arg, my_other_arg):
    """A function just for me.

    :param my_arg: The first of my arguments.
    :param my_other_arg: The second of my arguments.

    :returns: A message (just for me, of course).
    """

表格
----

=====  =====  =======
A      B      A and B
=====  =====  =======
False  False  False
True   False  False
False  True   False
True   True   True
=====  =====  =======

图片
----

.. image:: pic.jpg
   :height: 200px
   :width: 200 px
   :scale: 80 %
   :alt: alternate text
   :align: right


This is the caption of the figure (a simple paragraph).

The legend consists of all elements after the caption.  In this
case, the legend consists of this paragraph and the following

inline makeup
-------------

`inline makeup`

``inline makeup``

:guilabel:`inline makeup`

**inline makeup**

:class:`test_py_module.test.Foo`

:class:: Bar

:method:: Bar.quux()

This is a test. Here is an equation:
:math:`X_{0:5} = (X_0, X_1, X_2, X_3, X_4)`.
Here is another:

math
----

.. math::
    :label: This is a label

    \nabla^2 f =
    \frac{1}{r^2} \frac{\partial}{\partial r}
    \left( r^2 \frac{\partial f}{\partial r} \right) +
    \frac{1}{r^2 \sin \theta} \frac{\partial f}{\partial \theta}
    \left( \sin \theta \, \frac{\partial f}{\partial \theta} \right) +
    \frac{1}{r^2 \sin^2\theta} \frac{\partial^2 f}{\partial \phi^2}

You can add a link to equations like the one above :eq:`This is a label` by using ``:eq:``.

.. centered:: 居中显示