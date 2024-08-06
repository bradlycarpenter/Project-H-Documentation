
# File names

Use snake_case for file names. For named classes, convert the PascalCase class name to snake_case:

 This file should be saved as `weapon.gd`.
```
class_name Weapon
extends Node
```

 This file should be saved as `yaml_parser.gd`.
```
class_name YAMLParser
extends Object
```

# Classses

Use PascalCase for class names:
```
extends CharacterBody3D
```

Also use PascalCase when loading a class into a constant or a variable:
```
const Weapon = preload("res://weapon.gd")
```

This is the only instance where caps is used. For everything else it is lower case.
# Functions and variables[¶](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html#functions-and-variables "Permalink to this headline")

Use snake_case to name functions and variables:
```
var particle_effect
func load_level():
```

Constants in caps always.
Do not use an underscore before functions and variables made by yourself.

# Folders

All Lower Case
Snake Style "this_is_how_we_do_it"

# Assets

All lower case
Snake Style "this_is_how_we_do_it"
# Programming

## Ternary expressions

When you have particularly long `if` statements or nested ternary expressions, wrapping them over multiple lines improves readability.


```var angle_degrees = 135
var quadrant = (
		"northeast"
		if angle_degrees <= 90
		else "southeast"
		if angle_degrees <= 180
		else "southwest"
		if angle_degrees <= 270
		else "northwest"
)
```

## Avoid unnecessary parentheses

Avoid parentheses in expressions and conditional statements. Unless necessary for order of operations or wrapping over multiple lines, they only reduce readability.

Example:
```
if is_colliding():
	queue_free()
```

BAD:
```
if (is_colliding()):
	queue_free()
```

## Boolean operators

Prefer the plain English versions of boolean operators, as they are the most accessible:

- Use `and` instead of `&&`.
    
- Use `or` instead of `||`.
    
- Use `not` instead of `!`.

You may also use parentheses around boolean operators to clear any ambiguity. This can make long expressions easier to read.\

```
if (foo and bar) or not baz:
	print("condition is true")
```

### Numbers[¶](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html#numbers "Permalink to this headline")

Use lowercase for letters in hexadecimal numbers, as their lower height makes the number easier to read.

```
var hex_number = 0xfb8c0b
```

Do not follow the above style guide's recommendations regarding large numbers; type large numbers out instead:

```
var large_number = 1234567890
var large_hex_number = 0xfffff8f80000
var large_bin_number = 0b110100101010
var small_number = 12345
```

## Code order

This first section focuses on code order. For formatting, see [Formatting](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html#formatting). For naming conventions, see [Naming conventions](https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html#naming-conventions).

We suggest to organize GDScript code this way:
```
01. @tool
02. class_name
03. extends
04. # docstring

05. signals
06. enums
07. constants
08. @export variables
09. public variables
10. private variables
11. @onready variables

12. optional built-in virtual _init method
13. optional built-in virtual _enter_tree() method
14. built-in virtual _ready method
15. remaining built-in virtual methods
16. public methods
17. private methods
18. subclasses
```

This code order follows four rules of thumb:

1. Properties and signals come first, followed by methods.
2. Public comes before private.
3. Virtual callbacks come before the class's interface.
4. The object's construction and initialization functions, `_init` and `_ready`, come before functions that modify the object at runtime.

## Formatting

Use the editor default settings.


https://docs.godotengine.org/en/stable/tutorials/scripting/gdscript/gdscript_styleguide.html