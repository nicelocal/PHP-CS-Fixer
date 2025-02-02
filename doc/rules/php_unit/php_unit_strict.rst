========================
Rule ``php_unit_strict``
========================

PHPUnit methods like ``assertSame`` should be used instead of ``assertEquals``.

Warning
-------

Using this rule is risky
~~~~~~~~~~~~~~~~~~~~~~~~

Risky when any of the functions are overridden or when testing object equality.

Configuration
-------------

``assertions``
~~~~~~~~~~~~~~

List of assertion methods to fix.

Allowed values: a subset of ``['assertAttributeEquals', 'assertAttributeNotEquals', 'assertEquals', 'assertNotEquals']``

Default value: ``['assertAttributeEquals', 'assertAttributeNotEquals', 'assertEquals', 'assertNotEquals']``

Examples
--------

Example #1
~~~~~~~~~~

*Default* configuration.

.. code-block:: diff

   --- Original
   +++ New
    <?php
    final class MyTest extends \PHPUnit_Framework_TestCase
    {
        public function testSomeTest()
        {
   -        $this->assertAttributeEquals(a(), b());
   -        $this->assertAttributeNotEquals(a(), b());
   -        $this->assertEquals(a(), b());
   -        $this->assertNotEquals(a(), b());
   +        $this->assertAttributeSame(a(), b());
   +        $this->assertAttributeNotSame(a(), b());
   +        $this->assertSame(a(), b());
   +        $this->assertNotSame(a(), b());
        }
    }

Example #2
~~~~~~~~~~

With configuration: ``['assertions' => ['assertEquals']]``.

.. code-block:: diff

   --- Original
   +++ New
    <?php
    final class MyTest extends \PHPUnit_Framework_TestCase
    {
        public function testSomeTest()
        {
            $this->assertAttributeEquals(a(), b());
            $this->assertAttributeNotEquals(a(), b());
   -        $this->assertEquals(a(), b());
   +        $this->assertSame(a(), b());
            $this->assertNotEquals(a(), b());
        }
    }

Rule sets
---------

The rule is part of the following rule set:

- `@PhpCsFixer:risky <./../../ruleSets/PhpCsFixerRisky.rst>`_

Source class
------------

`PhpCsFixer\\Fixer\\PhpUnit\\PhpUnitStrictFixer <./../src/Fixer/PhpUnit/PhpUnitStrictFixer.php>`_
