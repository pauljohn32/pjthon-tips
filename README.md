# pjthon-tips
PJ Python Tips

I need to get more serious about translating programs written in R and
Objective C into Python, so I'll start a Tip sheet like I did when I
started translating SAS to R (http://pj.freefaculty.org/R/Rtips.html).


# Doc Sites that don't seem incorrect (so far)

1. [Python.org](https://docs.python.org/3/)

2. [Python-Course.eu](https://www.python-course.eu/python3_print.php):
Handy!


# Object Orientation

## Introspection: Ask an object for a list of methods that it can implement

See
https://stackoverflow.com/questions/34439/finding-what-methods-a-python-object-has/37464502

```
object_methods = [method_name for method_name in dir(object)
                  if callable(getattr(object, method_name))]
```

Note that used `dir(object)` to harvest all of the attributes from
object, and then fed all of those to `callable(getattr())` to find out
if they were callable attributes.  Compact coding!

Other thinks to keep in mind, 

* `dir()` for unstructures splat
* `isinstance(obj, type)` : are you one of those? 
* `issubclass(obj, super)` :

Suggestions further readings:

1. [Dive Into Python: Power of
Introspection](https://web.archive.org/web/20180901124519/http://www.diveintopython.net/power_of_introspection/index.html
"Introspection")

2. [Guide to Python introspection
   (IBM)](https://www.ibm.com/developerworks/library/l-pyint/index.html):
   **Warning** Python 2.2 code there.


Consider using this general purpose introspection function from the
IBM page:

```{python}
def interrogate(item):
    """IBM Python Introspection Function, updated for Python 3 by PJ."""
    if hasattr(item, '__name__'):
        print("NAME:    ", item.__name__)
    if hasattr(item, '__class__'):
        print("CLASS:   ", item.__class__.__name__)
        print("ID:      ", id(item))
        print( "TYPE:    ", type(item))
        print( "VALUE:   ", repr(item))
    if callable(item):
        print("CALLABLE:",  "Yes")
    else:
        print("CALLABLE:",  "No")
    if hasattr(item, '__doc__'):
        doc = getattr(item, '__doc__')
        doc = doc.strip()   # Remove leading/trailing whitespace.
        firstline = doc.split('\n')[0]
        print( "DOC:     ", firstline)
```


