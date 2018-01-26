---
layout: post
title: "TIL: Python Literal String Interpolation with F-strings"
category: til
tags: [python]
---
There are many ways to format strings in Python but as of version 3.6, f-strings offer a very simple and clean method for interpolating string literals:

```
>>> pi=3.14159
>>> print(f'pi is {pi}')
pi is 3.14159
```

Just as with `str.format()`, format specifiers may be used. For example:
```
>>> print(f'pi is {pi:.2f}')
pi is 3.14
```

Expressions between braces are evaluated too:
```
>>> print(f'pi squared is {pi ** 2}')
pi squared is 9.869587728099999
```

For more information and examples, see [PEP 498](https://www.python.org/dev/peps/pep-0498/)