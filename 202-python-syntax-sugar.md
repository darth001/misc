#


## random.shuffle
```
import random
x = range(100)
random.shuffle(x)
```

## enumerate
```
for i, d in enumerate(range(10)):
    print i, d
```

## ternary conditional operator
```
a = 1
b = 2
c = a if a > b else b
```

## with statement 

```
try:
    f = open("/path/to/file", 'r')
    print f.read()
finally:
    if f:
        f.close()
```

=>

```
with open("/path/to/file", 'r') as f:
    print f.read()
```

=>

```
class MyWith(object):
    def __enter__(self):
        print "Enter with"
        return self
    def __exit__(self, exc_type, exc_value, exc_traceback):
        if exc_traceback is None:
            print "Exited without Exception"
            return True
        else:
            print "Exited with Exception"
            return False

def test_with():
    with MyWith() as my_with:
        print "running my_with"
    
    print "--" * 32

    with MyWith() as my_with:
        print "running before Exception"
        raise Exception
        print "running after Exception"

if __name__ == "__main__":
    test_with()
```

## map
```
array = [1, 2, 3]
square_array = []
for i in array:
    square_array.append(i ** 2)
```

=>

```
array = [1, 2, 3]
square_array = map(lambda i: i ** 2, array)
```
or
```
array = [1, 2, 3]
square_arry = [i ** 2 for i in array]
```

## filter
```
array = [1, 2, 3, 4]
odds_array = filter(lambda i: i % 2, array)
```
or
```
array = [1, 2, 3, 4]
odds_array = [i for i in array if i % 2 != 0]
```

## reduce
```
array = [1, 2, 3, 4]
print reduce(lambda x, y: x + y, array)
print reduce(lambda x, y: x if x > y else y, array)
```
```
strings = ['abc', 'abcd', 'def']
print reduce(lambda count, str: count + str.count("abc"), strings, 0)
```

## eval
```
print eval("1 + 1")

def init():
    return 1
def func():
    return 2
action = {"num": init, "func": func}
expression = 'func(num)'
print eval(expression, action)
```

## decorator
```
def log(func):
    def wrapper(*args, **kwargs):
        print("call %s()" % func.__name__)
        return func(*args, **kwargs)
    return wrapper

@log
def func():
    print 'do something'
```

## yield

```
def fib(n):
    a = b = 1
    for i in range(n):
        yield a
        a, b = b, a + b

for i in fib(10):
    print i,


def func():
    while True:
        n = yield
        print n

gen = func()
print gen.next()
gen.send(2)
gen.send(3)
```

## for else
```
for i in range(100):
    if i > 10:
        print i
else:
    print "Can't find result"

```
















