.. _basics:

基础知识
==========

In :ref:`about`, we described what a schema is, and hopefully
justified the need for schema languages.  Here, we proceed to
write a simple JSON Schema.

In :ref:`about`, 我们通过写一个简单的JSON Schema来描述它是什么。

Hello, World!
-------------

When learning any new language, it's often helpful to start with the
simplest thing possible.  In JSON Schema, an empty object is a
completely valid schema that will accept any valid JSON.

当我们开始学习一门新的语言时，比较有效的办法是从简单着手。在JSON Schema这里，
一个空的对象就是完整的schema，并可以通过验证。

.. schema_example::

   { }
   --
   // This accepts anything, as long as it's valid JSON
   42
   --
   "I'm a string"
   --
   { "an": [ "arbitrarily", "nested" ], "data": "structure" }

|draft6|

You can also use ``true`` in place of the empty object to represent a schema
that matches anything, or ``false`` for a schema that matches nothing.

在第六版里，你可以使用``true``来代替空对象表示任何匹配的元素，使用``false``表示没有
任何匹配元素。

.. schema_example::

   true
   --
   // This accepts anything, as long as it's valid JSON
   42
   --
   "I'm a string"
   --
   { "an": [ "arbitrarily", "nested" ], "data": "structure" }

.. schema_example::

   false
   --X
   "Resistance is futile...  This will always fail!!!"

类型关键字 The type keyword
----------------

Of course, we wouldn't be using JSON Schema if we wanted to just
accept any JSON document.  The most common thing to do in a JSON
Schema is to restrict to a specific type.  The ``type`` keyword is
used for that.

实际上，我们会使用JSON Schema来严格限制指定的类型，`type`关键字就是做
这个的，如果不限制类型的话，就没必要使用Schema了。

.. note::

    When this book refers to JSON Schema "keywords", it means the
    "key" part of the key/value pair in an object.  Most of the work
    of writing a JSON Schema involves mapping a special "keyword" to a
    value within an object.

For example, in the following, only strings are
accepted:

.. schema_example::

   { "type": "string" }
   --
   "I'm a string"
   --X
   42

The ``type`` keyword is described in more detail in `type`.

Declaring a JSON Schema
-----------------------

Since JSON Schema is itself JSON, it's not always easy to tell when
something is JSON Schema or just an arbitrary chunk of JSON.  The
``$schema`` keyword is used to declare that something is JSON Schema.
It's generally good practice to include it, though it is not required.

.. note::
    For brevity, the ``$schema`` keyword isn't included in most of the
    examples in this book, but it should always be used in the real
    world.

.. schema_example::

    { "$schema": "http://json-schema.org/schema#" }

You can also use this keyword to declare which version of the JSON
Schema specification that the schema is written to.  See `schema` for
more information.

Declaring a unique identifier
-----------------------------

It is also best practice to include an ``$id`` property as a unique
identifier for each schema.  For now, just set it to a URL at a domain
you control, for example::

   { "$id": "http://yourdomain.com/schemas/myschema.json" }

The details of `id` become more apparent when you start `structuring`.

|draft6|

.. draft_specific::

    --Draft 4
    In Draft 4, ``$id`` is just ``id`` (without the dollar-sign).
