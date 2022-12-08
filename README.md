# fog
## Q: Что такое **итератор** и **итерируемый объект**?
## A:
Итерируемый объект: имеет методы `__iter__`, `__getitem__`

Итератор: имеет метод `__next__`

### Пример:
```python
class SimpleIterator:
    def __next__(self):
        return "hello"

for i in SimpleIterator():
    print(i)
```
### Возбуждается исключение:
```python
Traceback (most recent call last):                                                                                                                                         File "<stdin>", line 1, in <module>                                                                                                                                 TypeError: 'SimpleIterator' object is not iterable 
```

```python

class SimpleIterator:
    def __next__(self):
        return "hello"

class SimpleIterable:
    def __iter__(self) -> SimpleIterator:
        return SimpleIterator()

for i in SimpleIterable():
    print(i)
```

### Результат:
```
hello                                                                                                                                                                 hello                                                                                                                                                                 hello                                                                                                                                                                 hello                                                                                                                                                                 hello                                                                                                                                                                 hello                                                                                                                                                                 
...
```

### Другая реализация
```python
class SimpleIterable:
    def __iter__(self) -> SimpleIterator:
        return self
    def __next__(self): return "hello"
```
