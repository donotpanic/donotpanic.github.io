---
layout: post
title:  "Comprehensions in python"
date:   2020-08-16 17:00:00 -0700
categories: python comprehension
---
Comprehensions in python are a great tool to simplify iterating and creating lists.
They can increase readability when used right. But, be on the lookout for when they might reduce readability.
*Tip: Readability > Shortcuts*

The key to comprehensions is the syntax. Practice to become familiar with it.

## Table of contents <!-- omit in toc -->
- [List comprehension](#list)
- [Set comprehension](#set)
- [Dict comprehension](#dictionary)
- [Additional tips](#additional-tips)

## List

Using a for loop to double value of each number in the list:
```
my_list = [2, 4, 8]
new_list = []

for number in my_list:
    new_list.append(number * 2)

print(new_list)
```

Output:

> [4, 8, 16]

Using list comprehension:
```
my_list = [2, 4, 8]
new_list = [ number * 2 for number in my_list ]
print(new_list)
```

Breaking down the syntax:

> **[** number * 2 for number in my_list **]**
>
> We enclose within '[]' to return a list

> [ **number * 2** for number in my_list ]
>
> The first part is the expression. In a regular for loop expression comes afterwards.
> In list comprehension it comes first. This is the key to remembering the syntax.

> [ number * 2 **for number in my_list** ]
>
> The rest of the syntax looks very much like regular for loop: `for item in list`


## Set

Set comprehension follows same principal as lists. This will return a set (notice the curly braces):
```
my_list = [2, 4, 8]
new_list = { number * 2 for number in my_list }
print(new_list)
```

Output:

> {4, 8, 16}


## Dictionary

This will return a dict (notice the curly braces and key:value being returned)
```
my_dict = [2, 4, 8]
new_list = { number:number * 2 for number in my_dict }
print(my_dict)
```

Output:

> {2: 4, 4: 8, 8: 16}


## Additional tips

- Mix and match comprehensions with iterators:
    - We saw the example of iterating over a list and returning a list, set or dictionary.
    - You can mix n match. For example, iterate over dictionary and return a list.
    - You are able to iterate over any object with an iterator. [How to make an iterator](https://treyhunner.com/2018/06/how-to-make-an-iterator-in-python/)
- Nesting comprehensions
    - You can nest comprehensions. Best way to get comfortable with the syntax is practice and more practice.
    ```
    my_list = [[1, 2], [3], [5, 6]]
    new_list = [ num for my_sub_list in my_list for num in my_sub_list ]
    print(new_list)
    ```
    Output
    > [1, 2, 3, 5, 6]
    
    - It isn't the easiest thing to read. Key is breaking down its components.                                                                                                                                                                                                                                                                                              
- Comprehension with if
    - Pairing if with your comprehension can be a very powerful tool
    
    Only multiply by 2 numbers greater than 2:
    ```
    my_list = [2, 4, 8]
    new_list = [ number * 2 for number in my_list if number > 2 ]
    print(new_list)
    ```
    Output
    > [8, 16]
    
- Comprehension with ternary operator (<true> if <condition> else <false>)
    - You can combine comprehensions with ternary operator.
    - This is different from the above 'if'
    - More on the ternary operator in the upcoming blog.
- Using _ (underscore) for item
    - It is convention to use _ for item variable name if you are not using it.
    ```
    n = 100
    list_of_zeros = [ 0 for _ in range(n) ]
    ```
  
    - There is an easier and better way to do this without comprehensions.
    Above is just an example.
    ```
    list_of_zeros = [0] * n
    ```