.. Understanding JSON Schema documentation master file, created by
   sphinx-quickstart on Thu Sep  5 10:09:57 2013.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

深入理解 JSON Schema
=========================

JSON Schema is a powerful tool for validating the structure of JSON
data.  However, learning to use it by reading its specification is
like learning to drive a car by looking at its blueprints.  You don't
need to know how an electric motor fits together if all
you want to do is pick up the groceries.  This book, therefore, aims
to be the friendly driving instructor for JSON Schema.  It's for those
that want to write it and understand it, but maybe aren't interested
in building their own car---er, writing their own JSON Schema
validator---just yet.

JSON Schema 是一个很强大的用于验证JSON数据结构的工具。然而，学习使用它就像通过看汽车
设计图去学开车一样。你并不需要到杂货店里去把所有的汽车零件都配齐。这本书的目的就是引导
你如何轻松驾驶JSON Schema。它可以帮助你理解并如何更好的使用，但如果你对如何造一辆汽车
比较感兴趣的话，建议你去写一个JSON Schema验证器。

.. only:: html

    .. image:: _static/octopus.svg
        :alt: octopus
        :align: right

.. note::

    This book describes JSON Schema draft 7. Earlier versions of JSON Schema
    are not completely compatible with the format described here, but for the
    most part, those differences are noted in the text.

    这本书基于JSON Schema第七版草稿。它并不完全兼容以前的版本，但是大部分情况下都适用，
    如果遇到不同的地方，本书会注明。

**从何处开始?**

- This book uses some novel `conventions <conventions>` for showing
  schema examples and relating JSON Schema to your programming
  language of choice.

- 本书使用了一些与众不同`约定`，它用你所选择的编程语言来演示一些示例。

- If you're not sure what a schema is, check out `about`.

- 如果你还是不太清楚什么是schema，请查看`about`。

- `basics` chapter should be enough to get you started with
  understanding the core `reference`.

- `basics`章节可以满足你理解核心的`reference`

- When you start developing large schemas with many nested and
  repeated sections, check out `structuring`.

- 当你准备开发一个大型的schema，有很多嵌套的那种，请参考`structuring`

- `json-schema.org <http://json-schema.org>`__ has a number of
  resources, including the official specification and tools for
  working with JSON Schema from various programming languages.

- `json-schema.org <http://json-schema.org>`__ 是官方文档网站，里面有
  官方的文档标准和不同基于语言的JSON Schema工具

- `jsonschema.net <http://jsonschema.net>`__ is an online application
  run your own JSON schemas against example documents.  If you want to
  try things out without installing any software, it's a very handy
  resource.

- `jsonschema.net <http://jsonschema.net>`__ 是一个在线应用，你可以在上面
  运行你的JSON schema示例，尤其是你不想安装一个本地工具时十分有用。

.. only:: html

    Contents:

.. toctree::
   :maxdepth: 3

   conventions.rst
   about.rst
   basics.rst
   reference/index.rst
   structuring.rst

.. only:: html

   There is also a `print version of this document
   <http://json-schema.org/understanding-json-schema/UnderstandingJSONSchema.pdf>`__.

.. toctree::
   :maxdepth: 1

   credits.rst

.. only:: html

    * :ref:`genindex`
    * :ref:`search`
