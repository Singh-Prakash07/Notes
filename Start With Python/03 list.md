### List
+ A list is an ordered, mutable (changeable) collection that allows duplicate elements. Think of it as a flexible container where you can keep things in a specific sequence.
It can contain different data types (integers, strings, floats, or even other lists).
#### 1. Defining list
```
fruits = ["apple", "banana", "cherry"]
arr = [0]*n
arr = [0 for _ in range(n)] # list comprehensive
arr = list(map(int, input().split(" "))) or .split()
mixed_list = [1, "Hello", 3.4, True]
empty_list = []
```
Key Features:
+ Ordered: Maintains the order in which items are inserted.
+ Mutable: You can change, add, or remove items after creation.
+ Indexing: Access items via position (starting at 0).

#### 2. Accessing Elements (Indexing & Slicing)
+ Python lists are zero-indexed. You can access items using their position or a range of positions.
+ Positive Indexing: Starts from 0 (left to right).
+ Negative Indexing: Starts from -1 (right to left).
```
nums = [10, 20, 30, 40, 50]
print(nums[0])   # Output: 10
print(nums[-1])  # Output: 50 (last item)
```
##### Slicing
+ Slicing allows you to get a sub-section of a list using the syntax: `list[start : stop : step]`
+ start: Inclusive.
+ stop: Exclusive (it stops just before this index).
+ step: How many steps to skip (default is 1).
```
colors = ["red", "green", "blue", "yellow", "purple"]
print(colors[1:4])   # ['green', 'blue', 'yellow']
print(colors[:3])    # ['red', 'green', 'blue']
print(colors[::2])   # ['red', 'blue', 'purple'] (Every second item)
```
#### 3. Modifying a ListBecause lists are mutable, you can change them directly.ActionMethod/SyntaxExampleChange Itemlist[index] = new_valitems[0] = "New"Add to End.append(val)items.append("extra")Insert at Index.insert(index, val)items.insert(1, "middle")Combine Lists.extend(list2) or +list1.extend(list2)Remove by Value.remove(val)items.remove("apple")Remove by Index.pop(index)items.pop(2) (returns the item)Delete Indexdel list[index]del items[0]Clear All.clear()items.clear()4. Useful Built-in FunctionsThese functions work on the list as a whole:len(list): Returns the number of items.max(list) / min(list): Returns the largest or smallest value.sum(list): Adds up all numerical elements.sorted(list): Returns a new sorted list without changing the original.5. List ComprehensionThis is a "Pythonic" way to create new lists from existing iterables in a single line.Syntax: [expression for item in iterable if condition]Python# Create a list of squares for even numbers only
numbers = [1, 2, 3, 4, 5, 6]
squares = [x**2 for x in numbers if x % 2 == 0]

print(squares) # Output: [4, 16, 36]
6. Sorting and Reversing.sort(): Sorts the list permanently in ascending order. Use .sort(reverse=True) for descending..reverse(): Reverses the order of the list in place.
