# The Basics

## class
Basic class definitions begin with the keyword _class_, followed by a class name, followed by a pair of curly braces which enclose the definitions of the properties and methods belonging to the class.

A valid class name starts with a letter or underscore, followed by any number of letters, or underscores.

A class may contain its own constants, variables (called "properties"), and functions (called "methods").

### Example #1 Simple Class definition
```
<?php
class SimpleClass
{
  // property declaration
  public $var = 'a default value';

  // method declaration
  public function displayVar() {
    echo $this->var;
  }
}
?>
```
**This pseudo-variable ```$this```** is available when a method is called from within an object context. ```$this``` is a reference to the calling object.

### Example #2 Some examples of the _$this_ pseudo-variable

```
<?php
class A
{
  function foo()
  {
    if (isset($this)) {
      echo '$this is defined (';
      echo get_class($this);
      echo ")\n";
    } else {
      echo "\$this is not defined.\n";
    }
  }
}

class B
{
    function bar()
    {
      // Note: the next line will issue a warning if E_STRICT is enabled.
      A::foo();
    }
}

$a = new A();
$a->foo();

// Note: the next line will issue a warning if E_STRICT is enabled.
A::foo();
$b = new B();
$b->bar();

// Note: the next line will issue a warning if E_STRICT is enabled.
B::bar();
?>
```
The above example will output:
```
$this is defined (A)
$this is not defined.
$this is defined (B)
$this is not defined.
```
