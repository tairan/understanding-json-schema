.. index::
   single: $schema
   single: schema; keyword

.. _schema:

``$schema``关键字The $schema keyword
===================

The ``$schema`` keyword is used to declare that a JSON fragment is
actually a piece of JSON Schema.  It also declares which version of
the JSON Schema standard that the schema was written against.

``$schema``关键字用来声明这个JSON是一个Schema，同样也可以用来描述它使用的
是哪一个版本的标准来。

It is recommended that all JSON Schemas have a ``$schema`` entry,
which must be at the root.  Therefore most of the time, you'll want
this at the root of your schema::

推荐每个JSON Schema都包含``$schema``, 并将它放在根节点。大部分的时候，你
会在根节点放上你自己的schema。

    "$schema": "http://json-schema.org/schema#"

高级 Advanced
--------

If you need to declare that your schema was written against a specific version
of the JSON Schema standard, you should include the draft name in the path, for
example:

如果你需要指定特定版本的标准，你应该将草案名称包含在路径中，例如：

- ``http://json-schema.org/draft-07/schema#``
- ``http://json-schema.org/draft-06/schema#``
- ``http://json-schema.org/draft-04/schema#``

Additionally, if you have extended the JSON Schema language to include
your own custom keywords for validating values, you can use a custom
URI for ``$schema``.  It must not be one of the predefined values
above, and should probably include a domain name you own.

如果你想扩展JSON Schema，使用自定义的关键字去验证，你可以使用自定义的URI放在
``$schema``中，它不是上述示例中的哪些，而是你自己的域名。