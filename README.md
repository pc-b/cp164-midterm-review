# Stack_array
### is_empty
```python
return len(self._values) == 0
```

### combine
```python
while len(source1._values) > 0 and len(source2._values) > 0:
            self._values.append(source1.pop())
            self._values.append(source2.pop())
        while len(source1._values) > 0:
            self._values.append(source1.pop())
        while len(source2._values) > 0:
            self._values.append(source2.pop())

        return
```

### pop
```python
assert (len(self._values) > 0), 'Cannot pop from an empty stack'

        value = self._values.pop(len(self._values)-1)

        return value
```

### peek
```python
assert (len(self._values) > 0), 'Cannot peek at an empty stack'

        value = deepcopy(self._values[len(self._values)-1])

        return value
``` 

### push
```python
self._values.append(deepcopy(value))
        return
```

### reverse
```python
tempStack = deepcopy(self._values)
        while len(self._values) > 0:
            self.pop()
        while len(tempStack) > 0:
            self.push(tempStack.pop())
        return
```

### split_alt
```python
target1 = Stack()
        target2 = Stack()
        while len(self._values) > 0:
            target1._values.append(self._values.pop())
            if len(self._values) > 0:
                target2._values.append(self._values.pop())
        return target1, target2
```

# Queue_array
### combine
```python
while len(source1._values) > 0 and len(source2._values) > 0:
            self._values.append(source1._values.pop(0))
            self._values.append(source2._values.pop(0))
        while len(source1._values) > 0:
            self._values.append(source1._values.pop(0))
        while len(source2._values) > 0:
            self._values.append(source2._values.pop(0))
        return
```

### insert
```python
self._values.append(deepcopy(value))

        return
```

### is_empty
```python
return  len(self._values)  ==  0
```

### is_full
```python
return False
```

### is_identical
```python
if self._values != target._values:
            identical = False
        else:
            identical = True
        return identical
```

### peek
```python
assert (len(self._values) > 0), 'Cannot peek at an empty queue'

        value = deepcopy(self._values[0])

        return value
```

### split_alt
```python
target1 = Queue()
        target2 = Queue()
        while len(self._values) > 0:
            target1._values.append(self._values.pop(0))
            if len(self._values) > 0:
                target2._values.append(self._values.pop(0))
        return target1, target2
```

# Queue_circular
### is_empty
```python
return self._count == 0
```

### is_full
```python
return self._count == self._capacity
```
### len
```python
return self._count
```

### insert
```python
assert self._rear is not None, "Cannot add to a full queue"

        self._values[self._rear] = deepcopy(value)
       
        self._count += 1
        
        if self._front == None:
            self._front = self._rear
            
        if self._capacity == self._count:
            self._rear = None
            
        elif (self._capacity - 1) == self._rear:
            self._rear = 0
            
        else:
            self._rear += 1
        return
```

### remove
```python
assert self._front is not None, "Cannot remove from an empty queue"

        value = deepcopy(self._values[self._front])

        self._count -= 1
        
        if self._rear == None:
            self._rear = self._front
            
        if self._count == 0:
            self._front = None
            
        elif self._front == (self._capacity - 1):
            self._front = 0
            
        else:
            self._front += 1
            
        return value
```

### peek
```python
assert self._count > 0, "Cannot peek at an empty queue"

        value = deepcopy(self._values[self._front])
        return value
```

# Priority_Queue_array
### len
```python
return len(self._values)
```

### _set_first
```python
if len(self._values) == 0:
            self._first = None
        else:
            self._first = 0
            
            for i in range(0, len(self._values)):
                if self._values[self._first] > self._values[i]:
                    self._first = i
        return
```

### combine
```python
while len(source1._values) > 0 and len(source2._values) > 0:
            self._values.append(source1._values.pop(0))
            self._values.append(source2._values.pop(0))
        while len(source1._values) > 0:
            self._values.append(source1._values.pop(0))
        while len(source2._values) > 0:
            self._values.append(source2._values.pop(0))

        self._set_first()
        source1._set_first()
        source2._set_first()
        return
```

### insert
```python
self._values.append(deepcopy(value))
        
        if self._first == None:
            self._first = 0
        else:
            if self._values[self._first] > value:
                self._first = len(self._values) - 1
        return
```

### is_empty
```python
return len(self._values) == 0
```

### peek
```python
assert (len(self._values) > 0), 'Cannot peek at an empty priority queue'

        value = deepcopy(self._values[self._first])

        return value
```

### remove
```python
assert (len(self._values) > 0), 'Cannot remove from an empty priority queue'

        value = deepcopy(self._values.pop(self._first))
        self._set_first()
        
        return value
```

### split_alt
```python
target1 = Priority_Queue()
        target2 = Priority_Queue()
        
        while len(self._values) > 0:
            target1._values.append(self._values.pop(0))
            if len(self._values) > 0:
                target2._values.append(self._values.pop(0))

        self._set_first()
        target1._set_first()
        target2._set_first()
        
        return target1, target2
```

### split_key
```python
target1 = Priority_Queue()
        target2 = Priority_Queue()
        
        while len(self._values) > 0:
            num = self._values.pop(0)
            
            if key > num:
                target1._values.append(num)
            else:
                target2._values.append(num)
        
        self._set_first()
        target1._set_first()
        target2._set_first()
        
        return target1, target2
```