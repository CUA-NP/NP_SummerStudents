# GitHub, Jupyter, and Python

In this outline I will...

1. Give an introduction to... 
    * [GitHub](#github)
    * [Jupyter Notebook](#jnb)
2. [Present the basics of python](#python)
3. [Excercise](#ex)

**Note**: all my notes are for linux (which you can reproduce with a [linux subsystem](https://docs.microsoft.com/en-us/windows/wsl/install-win10), but I think the commands are the same with all os) <br>
**Also note**: I have zero experience with MacOS so ask Salina ;)

<a id='github'></a>
## GitHub

Three main uses for GitHub...

1. Store and backup code, including various versions of that code (i.e branches)
2. Share code easily with others (i.e. git clone)
3. Easily have multiple contributors working on one set of code

What not to use GitHub for...

* Backing up files, pictures, etc. (GitHub has a 1GB repository size limit)

### Installing GitHub

Follow the instructions [here](https://gist.github.com/derhuerst/1b15ff4652a867391f03)


### GitHub Terminology

* repository <br>
> A repository is like a folder for your project. Your project's repository contains all of your project's files and stores each file's revision history. You can also discuss and manage your project's work within the repository. <br>
e.g. https://github.com/trottar/CUA_summer_students <br>
[source](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/about-repositories) <br>
Note: there are remote repositories (i.e. online) and local repositories (i.e. on your machine)
* clone <br>
> cloning a copy of the repository to your local machine <br>
      git clone https://github.com/trottar/CUA_summer_students
* fork <br>
> make a copy of a repository in your own GitHub account
![](jnb_files/fork_1.png)
![](jnb_files/fork_2.png)
* branch <br>
> different versions of the repository
![](jnb_files/branch_1.png)
To check all branches in terminal...
      git branch -avv
To create new local branch...
      git branch <new_branch>
To change branches in the terminal...
      git checkout <new_branch>  
* status <br>
> To check the status of changes...
      git status      
* pull <br>
> Update your local repo with the remote one.
      git pull
* push <br>
> Update your remote repo with the local one.
      git push
* add <br>    
> To push changes they must first be added then commited...      
      git add <file>
To add all changes
      git add .
* commit <br>    
> Once you add the changes, you must commit them. It is good to commit with comments explaining the changes.
To commit with comments...
        git commit -m "<your_comments>"
* alias <br>
> The name of the remote you are pushing and pulling from. The default alias is called *origin*. It is customary to call your version of a repo *origin* and the original repo *upstream*. <br>
To set up a new alias...
      git remote add <new_alias>
To check current aliases...
      git remote -v
      
Now there is a lot more beyond this, but these are the main things starting out. 

One more useful feature is ignoring files from being added to remote repo <br>
1. Create a .gitignore file, in the terminal
       touch .gitignore
    
2. Edit .gitignore with whatever files you want to ignore <br>
       Note: You can ignore all of a certain type of file with * (e.g. *.png will ignore all png files)

<a id='jnb'></a>
## Jupyter Notebook

Jupyter notebook is a flexible software that allows one to...

1. Write-ups (e.g. pdfs, markdown files, etc.) 
       Note: This entire document was created in jupyter notebook
2. Run live code. This means I can put code directly into a jupyter notebook "cell" and it can produce an output directly in the notebook which can be put onto pdfs or whatever you want.

I will expand on 2 when I get into the python and c++ introduction.

### Installing Jupyter Notebook

Follow the instructions [here](https://jupyter.readthedocs.io/en/latest/install.html). This installation will also require you to install python, which we need anyways!

### Using Jupyter Notebook

Jupyter is very easy to use. The hardest part is the syntax, but that's why we have google!

![](jnb_files/jnb_1.png)

<a id='python'></a>
## Introduction to Python

Python is a great starting language because of it's easy syntax and intuitive coding scheme. I am not going to give a full course on python, but enough to understand what you're doing this summer!

### Basics of coding

Code in its basic form is just a way for you to talk to a computer. You must remember that computers are very stupid so programming languages convert our understanding of things into a format computers understand.

**Note**:By computers I am including firmware, OS, and other such technicalities, which in themselve are very important but beyond the scope of this quick intro.

Now there are many intricases and I am not even giving the broad strokes here, but for our purposes there are three main features of programming...
* Variable assignment
* _for_ loops
* functions/methods

With these three ideas you will be set for this summer.

#### Variables

Variables are how you store values. There are 4 types for our purposes...
1. Numbers (which includes floats, doubles, ints, etc.)
2. Strings
3. Arrays (which includes lists, numpy arrays, tuples, etc.)
4. Objects (which includes dictionaries, booleans, class callings, etc.)

In some languages, like C++, you must designate the type of variable, but luckily python you do not have to.

**Note**: You will have to designate the type of array as we will see in a bit.

#### _for_ loops

_for_ loops are iterative processes that can do a variety of things. A basic example is printing values of an array...


```python
# You make comments with a hashtag
# Below is an array called a list
a = [1,2,3,4]
# I am going to produce a for loop that will print the values of a
for val in a:
    # Notice how I must indent here. Indentation is a crucial aspect of python as it breaks down subprocesses.
    # Indents will occur in loops and methods/functions as we will see
    # the print will print the value of a (easy!)
    print(val)
```

    1
    2
    3
    4


You can also nest for loops for more complicated procedures. Although this is computationally expensive and time consuming.

Now I will take our list, a, and store the values into a new list, b. Then in a nested loop, I will print the new list. You will see how it grows!


```python
# First I need to create list b
b= [] 
# Notice how it is empty!
for a_val in a:
    b.append(a_val)
    for b_val in b:
        print(b_val)
    print("\n") # Prints a new line
# Now I will print a and b to see if they match
print(a)
print(b)
```

    1
    
    
    1
    2
    
    
    1
    2
    3
    
    
    1
    2
    3
    4
    
    
    [1, 2, 3, 4]
    [1, 2, 3, 4]


There are many faster ways to do loops in python, but we will learn about those later.

#### functions/methods

A function or method is a way to avoid writing the same code over and over again. Say for instance I wanted to perform the above nested loop with another array. I would have to copy and past all that code which over time can be tedious and make your code cumbersome.

A better way is using a method or function.

Let's get a little fancier now. We are going to use a thing called a package. In python these are modules that can be imported into your code. They have a variety of capabilities as we will see and is probably the best thing about python in my opinion. The package we will import is called Numpy and these are dynamic and fexible arrays with a variety of built in functions!


```python
# First we import numpy
import numpy as np
# Next instead of typing out all the elements of our array, numpy as a few great functions to speed things up!
a_new = np.arange(6)
# And like that we have made the equivalent of a_new = [0,1,2,3,4,5]
print(a_new)
```

    [0 1 2 3 4 5]



```python
# Now lets make our function
# We will call it loop_array(inp) and will take an argument called inp which is where we can insert our new array
def loop_array(inp):
    b_new= [] 
    for val in inp:
        b_new.append(val)
        for b_val in b_new:
            print(b_val)
        print("\n")
    print(inp)
    print(b_new)
    # all we need to do is return b_new and we have our function
    return b_new

# Now let's print our function with both a and a_new!

print("a",a,"a function",loop_array(a)) # See we can print multiple things in one print function!
print("a_new",a_new,"a_new function",loop_array(a_new))

```

    1
    
    
    1
    2
    
    
    1
    2
    3
    
    
    1
    2
    3
    4
    
    
    [1, 2, 3, 4]
    [1, 2, 3, 4]
    a [1, 2, 3, 4] a function [1, 2, 3, 4]
    0
    
    
    0
    1
    
    
    0
    1
    2
    
    
    0
    1
    2
    3
    
    
    0
    1
    2
    3
    4
    
    
    0
    1
    2
    3
    4
    5
    
    
    [0 1 2 3 4 5]
    [0, 1, 2, 3, 4, 5]
    a_new [0 1 2 3 4 5] a_new function [0, 1, 2, 3, 4, 5]


Hmmm, something looks weird between a_new and loop_array(a_new).

This is because we defined a_new as a numpy array and loop_array(a_new) as a list. The two are compatable but issues can arise. We can always make a_new a list by calling the built in list function...


```python
print(a_new)
print(list(a_new))
```

    [0 1 2 3 4 5]
    [0, 1, 2, 3, 4, 5]


### Plotting in python

There is a great python package called _matplotlib_ which allows one to make plots quickly and easily!

Let's start by plotting a vs a_new!


```python
import matplotlib.pyplot as plt

plt.plot(a,a_new)
# We need to label our axes and title our plot!
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
# Let's show our plot too!
plt.show()
```


    ---------------------------------------------------------------------------

    ValueError                                Traceback (most recent call last)

    <ipython-input-6-598065ae975e> in <module>
          1 import matplotlib.pyplot as plt
          2 
    ----> 3 plt.plot(a,a_new)
          4 # We need to label our axes and title our plot!
          5 plt.title('a_new vs a', fontsize =20)


    /usr/local/lib/python3.6/dist-packages/matplotlib/pyplot.py in plot(scalex, scaley, data, *args, **kwargs)
       2761     return gca().plot(
       2762         *args, scalex=scalex, scaley=scaley, **({"data": data} if data
    -> 2763         is not None else {}), **kwargs)
       2764 
       2765 


    /usr/local/lib/python3.6/dist-packages/matplotlib/axes/_axes.py in plot(self, scalex, scaley, data, *args, **kwargs)
       1644         """
       1645         kwargs = cbook.normalize_kwargs(kwargs, mlines.Line2D)
    -> 1646         lines = [*self._get_lines(*args, data=data, **kwargs)]
       1647         for line in lines:
       1648             self.add_line(line)


    /usr/local/lib/python3.6/dist-packages/matplotlib/axes/_base.py in __call__(self, *args, **kwargs)
        214                 this += args[0],
        215                 args = args[1:]
    --> 216             yield from self._plot_args(this, kwargs)
        217 
        218     def get_next_color(self):


    /usr/local/lib/python3.6/dist-packages/matplotlib/axes/_base.py in _plot_args(self, tup, kwargs)
        340 
        341         if x.shape[0] != y.shape[0]:
    --> 342             raise ValueError(f"x and y must have same first dimension, but "
        343                              f"have shapes {x.shape} and {y.shape}")
        344         if x.ndim > 2 or y.ndim > 2:


    ValueError: x and y must have same first dimension, but have shapes (4,) and (6,)



![png](output_13_1.png)


It seems we have come across our first error in python! The easiest way to fix these errors when you are first learning is copy and pasting the error into google. I then suggest looking for [stack overflow](https://stackoverflow.com/questions/43059482/python-valueerror-x-and-y-must-have-same-first-dimension) answers because people tend to give great explainations! 

According to our findings, we need to match the number of elements in a and a_new. This makes sense of course!

We have two routes to take...

* Subtract two elements from a_new
* Add two elements to a

Let's subtract the elements from a_new first...


```python
# We use the resize function of numpy to resize the array to the size we need (i.e. 4 elements)
a_new = np.resize(a_new,a_new.size-2)
print(a_new)

plt.plot(a,a_new)
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
plt.show()
```

    [0 1 2 3]



![png](output_15_1.png)


Let's now add two elements to a...


```python
# First let's redefine a_new so it has 6 elements again
a_new = np.arange(6)

# Next let's add two elements (4,5) to a
a  = np.append(a,(0,5))
print(a)

plt.plot(a,a_new)
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
plt.show()
```

    [1 2 3 4 0 5]



![png](output_17_1.png)


Hmm, it seems the order of our array has gotten a little messed up. We can either append 0 to the front and 5 to the back of the array or, in this case, we only care about numerical order so there is a numpy function for that!


```python
a = np.sort(a)
print(a)

plt.plot(a,a_new)
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
plt.show()
```

    [0 1 2 3 4 5]



![png](output_19_1.png)


Now two more things we can do with this data. We would like to see each point not them connected with a line so we will change our plot to a scatter one...


```python
plt.scatter(a,a_new)
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
plt.show()
```


![png](output_21_0.png)


The last thing we need is to fit the data! The data points are linear so we can use our classic linear fit (y=mx+b).


```python
# Define our slope and intercept
m,b = np.polyfit(a,a_new,1)

plt.scatter(a,a_new)
# Plot our fit
plt.plot(a, m*a + b)
plt.title('a_new vs a', fontsize =20)
plt.xlabel('a')
plt.ylabel('a_new')
plt.show()
```


![png](output_23_0.png)


<a id='ex'></a>
## Exercise

This should be a fairly simple excercise, but it will cover all the basics outlined. Use the resources you have available (Google is your best friend, especially [Stack Overflow](https://stackoverflow.com/). Also ask me on [slack](https://kaonlt.slack.com/) if you're stuck!

1. Fork a copy of the [CUA_summer_students](https://github.com/trottar/CUA_summer_students) repo into your own account
2. Clone that version into your local machine
3. Create a new remote and local branch called _develop_
4. In your local repo navigate to the [weekly_work/7_6_2020](weekly_work/7_6_2020) directory and create a new one called _excercise_
    * The rest of your work for this excercise will be done in here!
5. Create a new jupyter notebook called _hello_world.ipynb_
6. In this new jupyter notebook I want you to plot the following points...
    * pts = np.array([(1,2,3,4),(5,6,7,8)]) which is a 2D array (i.e. pts = [x,y])
7. Apply a linear fit 
8. Remove the 2nd element of x and the 3rd element of y
9. Plot your new x and y arrays but include the original x and y too
10. Linear fit the new x and y but include the original fit too
11. Push your changes to your GitHub repo
12. Post a link to your new directory in the Slack channel
