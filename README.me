# python-gostyle-defer
Python Go-Styled Defer

This original source is https://habrahabr.ru/post/191786/.
Thank you ограммирование.


# Go-style error handling

```Python
import inspect
import sys
from functools import wraps

def panic(x):
    raise Exception(x)

def defer(x):
    for f in inspect.stack():
        if '__defers__' in f[0].f_locals:
            f[0].f_locals['__defers__'].append(x)
            break

def recover():
    val = None
    for f in inspect.stack():
        loc = f[0].f_locals
        if f[3] == '__exit__' and '__suppress__' in loc:
            val = loc['exc_value']
            loc['__suppress__'].append(True)
            break
    return val

class DefersContainer(object):
    def __init__(self):
        # List for sustain refer in shallow clone
        self.defers = []

    def append(self, defer):
        self.defers.append(defer)

    def __enter__(self):
        pass

    def __exit__(self, exc_type, exc_value, traceback):
        __suppress__ = []
        for d in reversed(self.defers):
            try:
                d()
            except:
                __suppress__ = []
                exc_type, exc_value, traceback = sys.exc_info()
        return __suppress__


def with_defer(func):
    @wraps(func)
    def __wrap__(*args, **kwargs):
        __defers__ = DefersContainer()
        with __defers__:
            return func(*args, **kwargs)
    return __wrap__


@with_defer
def func():
    f = open('file.txt', 'w')
    defer(lambda: f.close())

    defer(lambda : print("Defer called!"))

    def my_defer():
        recover()

    defer(lambda: my_defer())

    print("Ok )")
    panic("WTF?")

    print("Never printed (((")


func()
print("Recovered!")
```
