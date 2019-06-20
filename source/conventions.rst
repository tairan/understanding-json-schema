.. _conventions:

本书使用约定 Conventions used in this book
=============================

语言规范提示 Language-specific notes
-----------------------

The names of the basic types in JavaScript and JSON can be confusing
when coming from another dynamic language.  I'm a Python programmer by
day, so I've notated here when the names for things are different from
what they are in Python, and any other Python-specific advice for
using JSON and JSON Schema.  I'm by no means trying to create a Python
bias to this book, but it is what I know, so I've started there.
In the long run, I hope this book will be useful to programmers of
all stripes, so if you're interested in translating the Python
references into Algol-68 or any other language you may know, pull
requests are welcome!

如果你用过其他动态语言，JavaScript和JSON中的基本类型名称可能会让你感到困惑。
我有Python的编程经验，这些内容跟Python的有所区别。在本书中，我并不是对Python
表示一种偏见。我希望本书对其他脚本语言的程序员有所帮助，如果你有兴趣移植Python
标准库到Algol-68或者其他语言，欢迎发送pull reqeusts。

The language-specific sections are shown with tabs for each language.
Once you choose a language, that choice will be remembered as you read
on from page to page.

在语言规范这个章节，列出了集中语言供选择参考，一旦你选中了某一个，建议你仔细
阅读。

For example, here's a language-specific section with advice on using
JSON in a few different languages:

举例，这里的语言规范章节建议你在以下几种不同的语言中使用JSON。

.. language_specific::

    --Python
    In Python, JSON can be read using the json module in the standard
    library.
    --Ruby
    In Ruby, JSON can be read using the json gem.
    --C
    For C, you may want to consider using `Jansson
    <http://www.digip.org/jansson/>`_ to read and write JSON.

草案规范提示 Draft-specific notes
--------------------

The JSON Schema standard has been through a number of revisions or "drafts". The
most important are Draft 7, the most recent at the time of this writing, and
Draft 4, on which a lot of production software was built, and the draft for
which an earlier version of this book was written.

JSON Schema标准有若干个版本或草案，其中草案7是最重要的，大部分内容都以此写成，草案4也
同样重要，很多产品软件都基于此开发，以及本书成书时的其他早期版本。

The text is written to encourage the use of Draft 7 and gives priority to the
latest conventions and features, but where it differs from earlier drafts, those
differences are highlighted in special call-outs. If you only wish to target
Draft 7, you can safely ignore those sections.

本书是以草案7以及最新的约定和功能写成，如果跟其他早期版本有冲突，本文会高亮显示。如果你
只关心草案7，那么你可以直接跳过这些提示。

|draft7|

.. draft_specific::

   --Draft 4
   This is where anything pertaining to an old draft would be mentioned.


示例 Examples
--------

There are many examples throughout this book, and they all follow
the same format.  At the beginning of each example is a short JSON
schema, illustrating a particular principle, followed by short JSON
snippets that are either valid or invalid against that schema.  Valid
examples are in green, with a checkmark.  Invalid examples are in red,
with a cross.  Often there are comments in between to explain why
something is or isn't valid.

本书提供了大量的示例，他们都使用相同的格式标准。在讲解示例之前，我们通过一个
简短的JSON片段来表述下验证结果的说明。我们会用绿色的✔来表示验证通过，对于
验证没通过的我们会用红色的❌来表示，通常，我们还会用注释来解释为什么没有通过
验证。

.. note::
    These examples are tested automatically whenever the book is
    built, so hopefully they are not just helpful, but also correct!

For example, here's a snippet illustrating how to use the ``number``
type:

.. schema_example::

    { "type": "number" }
    --
    42
    --
    -1
    --
    // Simple floating point number:
    5.0
    --
    // Exponential notation also works:
    2.99792458e8
    --X
    // Numbers as strings are rejected:
    "42"
