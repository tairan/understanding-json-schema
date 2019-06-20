.. index::
   single: null

.. _null:

null
----

The null type is generally used to represent a missing value.  When a
schema specifies a ``type`` of ``null``, it has only one acceptable
value: ``null``.

``null`` 类型通常表示不存在的值。当schema中指定一个``null``类型时，即表示它只接受
``null``null值

.. language_specific::

   --Python
   In Python, ``null`` is analogous to ``None``.
   在Python中，``null`` 即 ``None``
   --Ruby
   In Ruby, ``null`` is analogous to ``nil``.
   在Ruby中，``null`` 即 ``nil``

.. schema_example::

    { "type": "null" }
    --
    null
    --X
    false
    --X
    0
    --X
    ""
