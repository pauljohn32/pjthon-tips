# pjthon-tips
PJ Python Tips

I need to get more serious about translating programs written in R and
Objective C into Python, so I'll start a Tip sheet like I did when I
started translating SAS to R (http://pj.freefaculty.org/R/Rtips.html).


# Object Orientation

### Introspection: Ask an object for a list of methods that it can implement

See
https://stackoverflow.com/questions/34439/finding-what-methods-a-python-object-has/37464502

```
object_methods = [method_name for method_name in dir(object)
                  if callable(getattr(object, method_name))]
```

Suggestions further readings:


[Dive Into Python: Power of
Introspection](https://web.archive.org/web/20180901124519/http://www.diveintopython.net/power_of_introspection/index.html
"Introspection")



