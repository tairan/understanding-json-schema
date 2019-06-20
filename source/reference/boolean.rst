.. index::
   single: boolean

.. _boolean:

boolean
-------

The boolean type matches only two special values: ``true`` and
``false``.  Note that values that *evaluate* to ``true`` or ``false``,
such as 1 and 0, are not accepted by the schema.

布尔类型，只有两种值：``true`` 和 ``false``。注意，在schema中并不能用1和0来
替代它们。

.. language_specific::

   --Python
   In Python, "boolean" is analogous to ``bool``.  Note that in JSON,
   ``true`` and ``false`` are lower case, whereas in Python they are
   capitalized (``True`` and ``False``).
   在Python中，"boolean"和``bool``相似，注意，在JSON中使用全部小写，而在Python中
   他们使用首字母大写。
   --Ruby
   In Ruby, "boolean" is analogous to ``TrueClass`` and ``FalseClass``.  Note
   that in Ruby there is no ``Boolean`` class.
   在Ruby中，boolean和``TrueClass``、``FalseClass``相似。注意，在Ruby中没有
   ``Boolean``类。

.. schema_example::

    { "type": "boolean" }
    --
    true
    --
    false
    --X
    "true"
    --X
    // Values that evaluate to ``true`` or ``false`` are still not
    // accepted by the schema:
    0
