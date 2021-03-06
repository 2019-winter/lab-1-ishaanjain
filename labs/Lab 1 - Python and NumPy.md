---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Ishaan Jain


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**


Is Jupyter's kernel related to a kernel in the context of operating systems?


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
# YOUR SOLUTION HERE
import numpy as np
a = np.full((6, 4), 2, int)
print(a)
```

## Exercise 2

```python
# YOUR SOLUTION HERE
b = np.full((6,4), 1, int)
np.fill_diagonal(b, 3)
print(b)
```

## Exercise 3

```python
# YOUR SOLUTION HERE
print(a*b)
# print(np.dot(a,b))
# a*b works because element-wise multiplication requires the two matrices to have the same dimensions.
# np.dot(a,b) does not work because it requires the number of columns of the first matrix to equal the number of rows of the second matrix.
```

## Exercise 4

```python
# YOUR SOLUTION HERE
print(np.dot(a.transpose(),b))
print(np.dot(a,b.transpose()))
# The results are different shapes because the shape of the output matrix depends on the number of rows of the first matrix and number
# of columns of the second matrix.
```

## Exercise 5

```python
# YOUR SOLUTION HERE
def give_greeting():
    print('hi')
give_greeting()
```

## Exercise 6

```python
# YOUR SOLUTION HERE
def random_arrays():
    for i in range(0,3):
        a = np.random.randint(11,size=(5,5))
        print(a)
        print('sum:', np.sum(a))
        print('mean:', np.mean(a))
random_arrays()
```

## Exercise 7

```python
# YOUR SOLUTION HERE
def count_ones_v1(m):
    num_ones = 0
    for elem in np.ndarray.flatten(m):
        if elem == 1:
            num_ones += 1
    return num_ones
def count_ones_v2(m):
    num_ones = len(np.where(m==1)[0])
    return num_ones
rand_matrix = np.random.randint(11,size=(3,3))
print(count_ones_v1(rand_matrix))
print(count_ones_v2(rand_matrix))
```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
# YOUR SOLUTION HERE
import pandas as pd
a_8 = np.full((6, 4), 2, int)
a_8 = pd.DataFrame(a_8)
a_8
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
# YOUR SOLUTION HERE
a_9 = np.full((6,4), 1, int)
np.fill_diagonal(a_9, 3)
a_9 = pd.DataFrame(a_9)
a_9
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
# YOUR SOLUTION HERE
display(a_8*a_9)
# display(a_8.dot(a_9))
# a_8*a_9 works because element-wise multiplication requires the two matrices to have the same dimensions.
# a_8.dot(a_9) does not work because it requires the number of columns of the first matrix to equal the number of rows of the second matrix.
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
# YOUR SOLUTION HERE
def count_ones_v3(df):
    num_ones = 0
    for elem in df.values.flatten():
        if elem == 1:
            num_ones += 1
    return num_ones
def count_ones_v4(df):
    num_ones = df.where(df == 1).count().sum()
    return num_ones
rand_df = pd.DataFrame(np.random.randint(11,size=(3,3)))
print(count_ones_v3(rand_df))
print(count_ones_v4(rand_df))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
## YOUR SOLUTION HERE
display(titanic_df.loc[:, 'name'])
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
## YOUR SOLUTION HERE
titanic_df.set_index('sex',inplace=True)
female_only = titanic_df.loc['female']
display(female_only)
display(len(female_only))
```

## Exercise 14
How do you reset the index?

```python
## YOUR SOLUTION HERE
titanic_df = titanic_df.reset_index()
titanic_df
```

```python

```
