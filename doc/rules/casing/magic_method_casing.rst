============================
Rule ``magic_method_casing``
============================

Magic method definitions and calls must be using the correct casing.

Examples
--------

Example #1
~~~~~~~~~~

.. code-block:: diff

   --- Original
   +++ New
    <?php
    class Foo
    {
   -    public function __Sleep()
   +    public function __sleep()
        {
        }
    }

Example #2
~~~~~~~~~~

.. code-block:: diff

   --- Original
   +++ New
    <?php
   -$foo->__INVOKE(1);
   +$foo->__invoke(1);

Rule sets
---------

The rule is part of the following rule sets:

- `@PhpCsFixer <./../../ruleSets/PhpCsFixer.rst>`_
- `@Symfony <./../../ruleSets/Symfony.rst>`_

Source class
------------

`PhpCsFixer\\Fixer\\Casing\\MagicMethodCasingFixer <./../src/Fixer/Casing/MagicMethodCasingFixer.php>`_
