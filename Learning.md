BooK: https://practicalpython.yasoob.me/toc.html

Readme style guide: https://github.com/tchapi/markdown-cheatsheet/blob/master/README.md

# print(dir(type_of_data_structure)[::-1])
This will print all the available methods under the data structure

# for - else clause -> If the loop runs without hitting "break" then else clause will execute
https://book.pythontips.com/en/latest/for_-_else.html

# STRINGS

## RAW strings -> print(r'string_value') or print(R'string_value'), the escape characters are not effective
```
print(r'This is Mac Users// This is windows C:\\')
print('This is Mac Users// This is windows C:\\')
```

## how to replace a object in the string using the .replace(object, object1, count)

To remove a character, use the replace function and provide the number of occurrences to replace in the provided string
Strings are immutable objects which means you can change the char in string using the index number like s[8] = i

To replace it, either slice the string till the index number and add the desired char or value and then add up the rest of the 
string from the index numbers

                                                *OR*

Do the conversion to the list and replace the index value like list(object) -> list[8] -> ''.join(list(object))

## find() or rfind() || index() or rindex()
**Main difference is find or rfind will return -1 in case of no existence, whereas, the index or rindex will error out when
object doesn't exist in the string**

rfind() will return the object from the backwards, if multiple words exists with same name then it can be leveraged
rindex() is similar too rfind. **It's better to use rfind than rindex due to error handling**

## split() and splitlines()

- split(str=separator, number=string.count(str)) --> We can provide custom number in case if we want just few parts of the object instead of the all the parts in the object
```
>>> s = 'It yes or not yes'
>>> print(s.split(' ', 1))
['It', 'yes or not yes']
```

- splitlines() --> Here the separator is by default '\n' i.e. newline
```
>>> example_string = """
... This is what multi
... line string will look
... will use splitlines method
... """
>>> example_string.splitlines()
['', 'This is what multi', 'line string will look', 'will use splitlines method']
```

# TUPLES

## Usage of index() -> It is same as index, will return ValueError when there's no existence of the value
## Usage of count() --> It is same as count(), will return the occurrences of the value inside value based on the object given


# DICTIONARY

## Select certain number of objects in the dictionary using itertools

https://www.geeksforgeeks.org/python-get-first-n-keyvalue-pairs-in-given-dictionary/

dict(itertools.islice(dict_object.items(), N))

## Usage of items(), keys() and values()

- items() --> It is needed to iterate over the key value pairs in the dictionary
- keys() --> Will return list of the keys of the dict
- values() --> Will return list of the values of the dict

## Usage of pop() -> pop(key_object)
Dictionary pop method, this relies on the key value which has to be removed from the dictionary, if you would print the
operation which is doing the pop method, it would return the value assigned to the key

print(dict.pop(key)) -> value assigned to the key

## Usage of deepycopy() --> Another module import copy org_object = copy.deepcopy(object)

## Usage of copy()

This does the deepcopy which means the modifications done to either the newly copied dict or the original dict will be intact and changes won't be applied. Only when the values of the keys are not **iterable**
```
>>> old_dict_1 = {43:23, 6:56}
>>> new_dict_1 = old_dict_1.copy()
>>> new_dict_1
{43: 23, 6: 56}
>>> new_dict_1[43] = 10
>>> new_dict_1
{43: 10, 6: 56}
>>> old_dict_1
{43: 23, 6: 56}
>>> old_dict_1[6] = 120
>>> old_dict_1
{43: 23, 6: 120}
>>> new_dict_1
{43: 10, 6: 56}
```
*If the values of the dictionary keys are iterable say like list (When we are only appending the values to the list), then the values will be reflected in both the original and newly copied dictionary. The values will not be reflected if the value of the key is completely assigned a new list*

https://moonbooks.org/Articles/How-to-copy-a-dictionary-in-python-/

## Usage of '=' for dictionary

This does the shallow copy of the dict, which means if the original dictionary is changed, then the new dictionary object will reflect the change too

old_dict = {1:2, 4:5} --> new_dict = old_dict --> new_dict = {1:2, 4:5} if I update the old_dict value old_dict = {1:2, 4:8} then new_dict will be {1:2, 4:8}
```
>>> old_dict = {1:2, 4:5}
>>> new_dict = old_dict
>>> new_dict
{1: 2, 4: 5}
>>> new_dict[4] = 10
>>> old_dict
{1: 2, 4: 10}
>>> new_dict
{1: 2, 4: 10}
```

## Usage of the update()

In case, if we have to include the contents of the one dictionary into another, then update method must be used
```
dit = {5: 2, 0: 10}
dit_2= {1: 2, 4: 10}
dit.update(dit_2)
dit = {5: 2, 0: 10, 1: 2, 4: 10} 
```

## Usage of the OrderedDict(), the method move_to_end()

OrderedDict() retains the order of the key value pairs in the dict, since dict is unordered to begin with

from collections import OrderedDict()

move_to_end(object, last=True or False)
- object is the key of the dictionary
- True means, the key will be sent to the end of the dictionary
- False means, the key will be at the front of the dictionary


# LISTS

## reverse()  --> It will reverse the list and but have to do before operation depending on it
```
A = [1,3,5,2]
A.reverse()
print(A)
[2,5,3,1]
```
**If the result needs to be printed reverse then use [::-1], as it doesn't need multiple definitions like reverse function print(A[::-1])**

## sort() --> It will sort the list but will have to do before the operation
```
A = [1,54,3,40]
A.sort()
print(A)
[1,3,40,54]

print(A.sort()) -> This will print None as the sort() doesn't return, unlike sorted(object)
```
**If the print the result has to be printed, then use sorted(A)**

## remove() --> It only removes the first occurrences and this doesn't work on list[::-1].remove(object)


## List comprehension

- [ele if condition_true for ele in elements]
- [ele if condition_true else none for ele in elements] --> It is limited, as the X +=1 or X -= 1 doesn't work if the condition is succeeded.

# SETS

# CLASSES

https://book.pythontips.com/en/latest/__slots__magic.html

Usage of the __slots__ before the __init__ method but new type of the class has to be in use
- class(object) --> new style
- class() --> old style


# ZIP zip(obj1, obj2, obj3, strict=True) Function

```
>>> names = ["Louvre", "Diagon Alley", "Saturn V", "Millennium Falcon", "NYC"]
>>> set_numbers = ["21024", "75978", "92176", "75192", "21028"]
>>> num_pieces = [695, 5544, 1969, 7541, 598]
>>> list(zip(names, set_numbers, num_pieces))
[('Louvre', '21024', 695), ('Diagon Alley', '75978', 5544), ('Saturn V', '92176', 1969), ('Millennium Falcon', '75192', 7541), ('NYC', '21028', 598)]
```
- ** In case if one of the object length is shorter than rest of two objects, then it will result in error, it's applicable when you expect all the objects length to be same, we can use strict=True**

## **Conversion into the list or dictionary can be done on the zip object dict(zip(obj1, obj2)) or list(zip(obj1, obj2))**


# MAP Function

map(function, list_of_inputs), mostly the function is the lambda itself

# COLLECTIONS MODULE

- defaultdict()

- OrderedDict() --> Will ensure the items in the dictionary are iterated in an order -- OrderedDict(list_of_tuples) OrderedDict([(1,1),(4,4)])

- deque() --> It can use to remove elements from either end. popleft() or pop (which is default) or extendleft()

- Counter() --> will count the items
    print(Counter('abdcdqeaaa'))

- It will give the result in the decreasing order based on number of occurrences
- **Usage of the most_common(number)  -> To get the top value in Counter or values depending up on the number to extract it**

- namedTuple --> Usage of the positional argument is significant (*object (a b c) or list ['a', 'b', 'c'])
```
example = namedtuple('example', 'key1 key2 key3')
example1 = example(key1='A', key2='B', key3='C')
```
- Also, can set the default values to the keys given in the namedtuple and those values are set from right most means (key3, key2,..)
```
sample = namedtuple("sample", "x,y,z", defaults=[0,0])
print(sample(1))   --> sample(x=1, y=0, z=0) -- As we see only two default values are provided so the value for 'x' has to be defined or error out.
```
- Interesting aspect, when the key cannot be appended to the example1 then use the _fields.index and __get_item__
```
from collections import namedtuple
items = [["phone","blue","pixel"],["computer","silver","lenovo"],["phone","gold","iphone"]]
count, ruleKey = 0, "color"
items_match = namedtuple('items_match', "type color name")
output = [items_match(*item) for item in items]
for select in output:
    print(select.ruleKey)   --> This doesn't work since under the select this is how the object is items_match(type='phone', color='gold', name='iphone'). As we see there is no ruleKey as a key, even though we assumed that the value assigned to the ruleKey will be considered.
```
print(select.__getitem__(select._fields.index(ruleKey)))
```
from collections import namedtuple
items = [["phone","blue","pixel"],["computer","silver","lenovo"],["phone","gold","iphone"]]
count, ruleKey = 0, "color"
items_match = namedtuple('items_match', "type color name")
output = [items_match(*item) for item in items]
for select in output:
    print(select.__getitem__(select._fields.index(ruleKey)))
```



# DEBUGGING

- import pdb > pdb.set_trace()

- You can get the interactive shell python -i file.py

# LOGICAL OPERATORS

- ^ XOR (True & True = True, True & False = False False & False = False)
- // (Divisor)
```
2//20 -> 0
21//20 -> 1
```
- % (Reminder)
```
2%20 -> 2
21%20 -> 1
```

- Consider the infinity value when initially comparing the min and max value to it get going in the list: float('inf')


# MISC

list(filter(function, list_of_inputs)) --> returns true or false based on the function logic and inputs

sort vs sorted

sort --> the modifications occurs on the provided list itself
sorted --> the list provided as the parameter remains untouched, and a new list is the resultant

In the functions, the default arguments are evaluated only once, so up on each call, the default arguments won't be
initialized every time
 https://book.pythontips.com/en/latest/mutation.html


class A():  --> This is a class (which in python can also be stated as an object)

    def __init__(self, arg1, arg2): (__init__ this is called when the class is instantiated i.e. when you declare a class ) ref: https://towardsdatascience.com/enhance-your-python-project-code-with-classes-5a19d0e9f841
        self.arg1 = arg1      (self.arg1 --> instances attributes  arg1 = is the argument value passed through the class initialization)
        self.arg2 = arg2      (self.arg2 --> instances attributes  arg2 = is the argument value passed through the class initialization)


Ex:

class A():

    def __init__(self, arg1, arg2):
        self.arg1 = arg1
        self.arg2 = arg2

    def sum():
        return self.arg1 + self.arg2

print(A(3,4).sum())

https://www.pypy.org
