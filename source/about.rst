.. _about:

schema 是什么？ What is a schema?
=================

If you've ever used XML Schema, RelaxNG or ASN.1 you probably already
know what a schema is and you can happily skip along to the next
section.  If all that sounds like gobbledygook to you, you've come to
the right place.  To define what JSON Schema is, we should probably
first define what JSON is.

如果你已经使用过XML Schema, 那你可能已经知道schema是什么了，你可以直接跳过
下面的章节。如果你觉得还是不太懂，那来这里就对了。若要定义JSON Schema是什么，
首先要定义什么是JSON。

JSON stands for "JavaScript Object Notation", a simple data
interchange format.  It began as a notation for the world wide web.
Since JavaScript exists in most web browsers, and JSON is based on
JavaScript, it's very easy to support there.  However, it has proven
useful enough and simple enough that it is now used in many other
contexts that don't involve web surfing.

JSON标准里说JSON是JavaScript对象表示符号，一个简单的数据交换格式。它开始用在
万维网，因为JavaScript是浏览器里的事实标准，各种浏览器都支持，因此JSON基于
JavaScript会很容易被支持。然而，现在它被用到了更多地方，不再局限于浏览器了。

At its heart, JSON is built on the following data structures:

下面的数据结构，可以很清楚的表示JSON的核心。

- object::

  { "key1": "value1", "key2": "value2" }

- array::

  [ "first", "second", "third" ]

- number:

  .. code-block:: text

     42
     3.1415926

- string:

  .. code-block:: text

     "This is a string"

- boolean:

  .. code-block:: text

     true
     false

- null:

  .. code-block:: text

     null

These types have analogs in most programming languages, though they
may go by different names.

这些类型跟其他编程语言类似，也许只是叫法的不同。

.. language_specific::

    --Python
    The following table maps from the names of JavaScript types to
    their analogous types in Python:

    下表是跟Python 类型相对应的关系

    +----------+-----------+
    |JavaScript|Python     |
    +----------+-----------+
    |string    |string     |
    |          |[#1]_      |
    +----------+-----------+
    |number    |int/float  |
    |          |[#2]_      |
    +----------+-----------+
    |object    |dict       |
    +----------+-----------+
    |array     |list       |
    +----------+-----------+
    |boolean   |bool       |
    +----------+-----------+
    |null      |None       |
    +----------+-----------+

    .. rubric:: Footnotes

    .. [#1] Since JavaScript strings always support unicode, they are
            analogous to ``unicode`` on Python 2.x and ``str`` on
            Python 3.x.

    .. [#2] JavaScript does not have separate types for integer and
            floating-point.

    --Ruby
    The following table maps from the names of JavaScript types to
    their analogous types in Ruby:

    这里是跟Ruby类型的对应关系表

    +----------+----------------------+
    |JavaScript|Ruby                  |
    +----------+----------------------+
    |string    |String                |
    +----------+----------------------+
    |number    |Integer/Float         |
    |          |[#3]_                 |
    +----------+----------------------+
    |object    |Hash                  |
    +----------+----------------------+
    |array     |Array                 |
    +----------+----------------------+
    |boolean   |TrueClass/FalseClass  |
    +----------+----------------------+
    |null      |NilClass              |
    +----------+----------------------+

    .. rubric:: Footnotes

    .. [#3] JavaScript does not have separate types for integer and
            floating-point.

With these simple data types, all kinds of structured data can be
represented.  With that great flexibility comes great responsibility,
however, as the same concept could be represented in myriad ways.  For
example, you could imagine representing information about a person in
JSON in different ways::

使用这些简单的数据类型，通过结构化的组织，它可以表述无数种类型。比如，你可以
用JSON来描述一个person。

    {
      "name": "George Washington",
      "birthday": "February 22, 1732",
      "address": "Mount Vernon, Virginia, United States"
    }

    {
      "first_name": "George",
      "last_name": "Washington",
      "birthday": "1732-02-22",
      "address": {
        "street_address": "3200 Mount Vernon Memorial Highway",
        "city": "Mount Vernon",
        "state": "Virginia",
        "country": "United States"
      }
    }

Both representations are equally valid, though one is clearly more
formal than the other.  The design of a record will largely depend on
its intended use within the application, so there's no right or wrong
answer here.  However, when an application says "give me a JSON record
for a person", it's important to know exactly how that record should
be organized.  For example, we need to know what fields are expected,
and how the values are represented.  That's where JSON Schema comes
in.  The following JSON Schema fragment describes how the second
example above is structured.  Don't worry too much about the details
for now.  They are explained in subsequent chapters.

这两种描述都是有效的，下面的会比上面的描述的更清晰一些。定义一个类型，它的复杂
程度取决于不同的应用场景，简单还是复杂并不是对与错的关系。然而，当一个程序说“
给我一个person的JSON对象时，它期望的是一个精准描述的格式。比如，期望哪些字段
应该存在，以及它的值是什么类型的。这个时候JSON Schema就派上用场了。下面就通过
示例来描述一个schema，我们会在其他章节进一步详解。

.. schema_example::

    {
      "type": "object",
      "properties": {
        "first_name": { "type": "string" },
        "last_name": { "type": "string" },
        "birthday": { "type": "string", "format": "date" },
        "address": {
          "type": "object",
          "properties": {
            "street_address": { "type": "string" },
            "city": { "type": "string" },
            "state": { "type": "string" },
            "country": { "type" : "string" }
          }
        }
      }
    }
    --X
    // By "validating" the first example against this schema, you can
    // see that it fails:
    {
      "name": "George Washington",
      "birthday": "February 22, 1732",
      "address": "Mount Vernon, Virginia, United States"
    }
    --
    // However, the second example passes:
    {
      "first_name": "George",
      "last_name": "Washington",
      "birthday": "22-02-1732",
      "address": {
        "street_address": "3200 Mount Vernon Memorial Highway",
        "city": "Mount Vernon",
        "state": "Virginia",
        "country": "United States"
      }
    }

You may have noticed that the JSON Schema itself is written in JSON.
It is data itself, not a computer program.  It's just a declarative
format for "describing the structure of other data".  This is both its
strength and its weakness (which it shares with other similar schema
languages).  It is easy to concisely describe the surface structure of
data, and automate validating data against it.  However, since a JSON
Schema can't contain arbitrary code, there are certain constraints on
the relationships between data elements that can't be expressed.  Any
"validation tool" for a sufficiently complex data format, therefore,
will likely have two phases of validation: one at the schema (or
structural) level, and one at the semantic level.  The latter check
will likely need to be implemented using a more general-purpose
programming language.

前面我们提到了JSON Schema就是JSON，而JSON则是数据，并不是代码。它只是定义了
一个描述另一个数据应该是什么格式。这既是它的优点同样也是缺点所在。它可以轻松
地去描述一个数据的结构，并且支持自动化的验证。然而JSON Schema并不包含任何
代码，数据之间的约束关系就不方便限制。任何一个”验证工具”都是用来处理复杂的数据
格式的，我们有两个阶段去做验证，一个是结构验证，另一个是语义验证。后面的一个验证
由很其他编程语言来实现。