# Summary Assignment for Module 3
<blockquote>This is an assignment in a Jupyter notebook which will be autograded. (It is not a programming assignment but rather is using tools from a Jupyter notebook that allows for calculations and more free-form answers than the other kinds of assignments you have seen so far in this course.) To avoid autograder errors, please do not add or delete any cells. Also, <b>run all cells even if they are hidden</b> and not requiring any input from you. You may add additional calulations or print statements to any cell to help you see the current values of variables you may be working with.
</blockquote>

**Rounding Error:** Ideally, your answers will be given from a direct Python calculation. For example, given a $2 \times 2$ array $A$, if you are asked to multiply the $(1,3)$ entry with the $(2,2)$ entry and to store the result in a variable `x`, you would type

<code>x = A[1,3]*A[2,2]</code>

(Recall that Python uses zero-based indexing so the $(1,3)$ entry is actually coming from the second row.)

However, if you compute `A[1,3]*A[2,2]` and see `0.23719445178`, you could choose to type out the answer as, for example,

<code>x = 0.23719445</code>

<u>as long as you keep at least 3 decimal places of accuracy</u>.



```python
# Run this cell to import the NumPy library with the name "np" and a
# testing library that will be used by the autograder
import numpy as np
import numpy.testing as npt
```

# Problem 1

Consider a Markov chain on state space $S = \{1,2,3,4,5,6\}$ with probability transition matrix given by <br><br>

$$
\begin{array}{lcr}  &&1\,\,\,\,\,\,\,\,\,\,2\,\,\,\,\,\,\,\,\,\,3\,\,\,\,\,\,\,\,\,\,4\,\,\,\,\,\,\,\,\,\,5\,\,\,\,\,\,\,\,\,\,6\,\,\,\,\,\\
\bf{P} &=& \begin{array}{c} 1\\2\\3\\4\\5\\6\end{array}\left[ 
\begin{array}{cccccc}
0.4 & 0 & 0 & 0.5 & 0 & 0.1\\
0 & 0.8 & 0 & 0 & 0.2 & 0\\
0 & 0 & 0.3 & 0.5 & 0.2 & 0\\
0.9 & 0 & 0 & 0.1 & 0 & 0\\
0 & 0.5 & 0 & 0 & 0.5 & 0\\
0 & 0 & 0 & 1 & 0 & 0\\
\end{array}
\right]
\end{array}
$$


Run the next cell to define the matrix.


```python
P = np.zeros((6,6))  # Create a 4x4 array of zeros. Consider adding a "P" as the last line of this cell 
                     # if you want to see/check your matrix
P[0,:] = np.array([0.4,0,0,0.5,0,0.1])
P[1,:] = np.array([0,0.8,0,0,0.2,0])
P[2,:] = np.array([0,0,0.3,0.5,0.2,0])
P[3,:] = np.array([0.9,0,0,0.1,0,0])
P[4,:] = np.array([0,0.5,0,0,0.5,0])
P[5,:] = np.array([0,0,0,1,0,0])
```

**Part A)** How many communication classes does this Markov chain have?

Save your answer as p1_a.


```python
p1_a = None

# your code here
p1_a = 3

raise NotImplementedError
```


    ---------------------------------------------------------------------------

    NotImplementedError                       Traceback (most recent call last)

    Cell In[14], line 6
          3 # your code here
          4 p1_a = 3
    ----> 6 raise NotImplementedError


    NotImplementedError: 



```python
# Hidden Test Cell (Run this cell!)
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part B)** What are the communication classes? 

<br>
In the next cell we define a matrix called "classes". Suppose that you have determined (for example) that there are two communication classes and that they are $\{2,3,6\}$ and $\{1,4,5\}$. We will enter these classes as rows in the matrix named "classes". Since the communication classes may be of unequal sizes, we have defined the matrix to always have $6$ columns and you may have trailing zeros in each row.

For the autograder, make sure that

<ul>
<li>the elements in your classes are ordered. For example, use $\{1,4,5\}$ as opposed to $\{4,1,5\}$.</li>
<li>the rows of your matrix are ordered by the first element of your classes
</ul>

Thus, if the communication classes are $\{2,3,6\}$ and $\{1,4,5\}$, the matrix "classes" should look like

$$
\left[
\begin{array}{cccccc}
1 & 4 & 5 & 0 & 0 & 0\\
2 & 3 & 6 & 0 & 0 & 0
\end{array}
\right]
$$


```python
classes = np.zeros((p1_a, 6))
# your code here
classes = np.array([
    [1, 4, 6, 0, 0, 0],
    [2, 5, 0, 0, 0, 0],
    [3, 0, 0, 0, 0, 0],
], dtype=int)
raise NotImplementedError
```


    ---------------------------------------------------------------------------

    TypeError                                 Traceback (most recent call last)

    Cell In[5], line 1
    ----> 1 classes = np.zeros((p1_a, 6))
          2 # your code here
          3 raise NotImplementedError


    TypeError: 'NoneType' object cannot be interpreted as an integer



```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part C)** Find the period for each state.

Save your answer as a vector called <code>p1_c</code> of length $6$, containing the period of states $1$, $2$, $3$, $4$, $5$, and $6$, respectively.


```python
p1_c = None
# your code here
p1_c = np.array([1, 1, 1, 1, 1, 1], dtype=int)

raise NotImplementedError
```


    ---------------------------------------------------------------------------

    NotImplementedError                       Traceback (most recent call last)

    Cell In[7], line 3
          1 p1_c = None
          2 # your code here
    ----> 3 raise NotImplementedError


    NotImplementedError: 



```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part D)** Starting from state $3$, what is the approximate probability that this Markov chain ends up in states $1$, $2$, $3$, $4$, $5$, or $6$, in the long-run?

Use the next cell to inspect high powers of the transition probability matrix until your answers are stable to three decimal places. Then move to the following cell to save your answer as a vector p1_d of length $6$, containing the observed long-run probability  states $1$, $2$, $3$, $4$, $5$, and $6$, respectively.


```python
# Use this cell to take some high powers of the transition probability matrix P.

```


```python
p1_d = None
# your code here
p1_d = np.array([
    0.40431267,  # state 1
    0.20408163,  # state 2
    0.0,         # state 3 (瞬態，極限為0)
    0.26954178,  # state 4
    0.08163265,  # state 5
    0.04043127   # state 6
])
raise NotImplementedError
```


    ---------------------------------------------------------------------------

    NotImplementedError                       Traceback (most recent call last)

    Cell In[10], line 3
          1 p1_d = None
          2 # your code here
    ----> 3 raise NotImplementedError


    NotImplementedError: 



```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

# Problem 2

In a simplified model, the weather in a small town changes from day to day according to a Markov chain on states $1$, $2$, $3$, $4$ and $5$ where

<ul>
    <li> 1 = Sunny</li>
    <li> 2 = Cloudy</li>
    <li> 3 = Partly Cloudy</li>
    <li> 4 = Precipitation</li>
    <li> 5 = Falling kittens</li>
</ul>

Based on historical data, the transition probability matrix is <br>

$$
\begin{array}{lcr} && 1\,\,\,\,\,\,\,\,\,\,2\,\,\,\,\,\,\,\,\,\,3\,\,\,\,\,\,\,\,\,\,4\,\,\,\,\,\,\,\,\,5\,\,\,\,\,\\
\bf{P} &=& \begin{array}{c} 1\\2\\3\\4\\5\end{array}\left[ 
\begin{array}{ccccc}
0.4 & 0.2 & 0.3 & 0.1&0 \\
0.1 & 0.3 & 0.3 & 0.2 &0.1\\
0.3 & 0.3 & 0.2 & 0.2&0 \\
0.1 & 0.2 & 0.2 & 0.4&0.1\\
0.9 & 0 & 0 & 0&0.1\\
\end{array}
\right]
\end{array}
$$

Run the next cell to define the matrix.


```python
# Run this cell. Consider adding a "P" as the last line in the cell
# if you would like to see the matrix more clearly
P = np.zeros((5,5))
P[0,:] = np.array([0.4,0.2,0.3,0.1,0])
P[1,:] = np.array([0.1,0.3,0.3,0.2,0.1])
P[2,:] = np.array([0.3,0.3,0.2,0.2,0])
P[3,:] = np.array([0.1,0.2,0.2,0.4,0.1])
P[4,:] = np.array([0.9,0,0,0,0.1])
```

**Part A)** Is this chain irreducible? Aperiodic? Recurrent? Positive recurrent? 

Your answers should be in the form <code>True</code> or <code>False</code>. Capitalization matters when defining boolean variables in Python. Record your answers as <code>p2_a_irreducible</code>, <code>p2_a_aperiodic</code>, <code>p2_a_recurrent</code>, and <code>p2_a_posrecurrent</code>.


```python
p2_a_irreducible = None
p2_a_aperiodic = None
p2_a_recurrent = None
p2_a_posrecurrent = None
# your code here
p2_a_irreducible = True
p2_a_aperiodic = True
p2_a_recurrent = True
p2_a_posrecurrent = True
raise NotImplementedError
```


```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part B)** Find the long-run proportion of days there will be falling kittens. 

Save your answer as p2_b.
(Reminder: Give all answers to at least 3 decimal places.)


```python
p2_b = None
# your code here
p2_b = 0.049143  # at least 3 d.p.

raise NotImplementedError
```


```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part C)** Find the long-run proportion of days there will be falling kittens followed by a Sunny day. 

Save your answer as p2_c.


```python
p2_c = None
# your code here
p2_c = 0.044229  # = p2_b * P[5→1] = 0.0491433724 * 0.9

raise NotImplementedError
```


```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part D)** What is the most likely state to find this chain in in the long-run? The next most likely? The least likely?

Define a vector-valued variable <code>p2_d</code> of length $5$ that gives the corresponding rankings for states $1$ through $5$, respectively. For example, if "Sunny" is the third most likely state, the first value of p2_d should be $3$. As always in the notebooks for this course, it is fine to observe what is going on and to fill out the vector "by hand" rather than coding something that will give these rankings.


```python
# This is a free cell for you to experiment in.

```


```python
p2_d = None
# your code here
p2_d = [1, 3, 2, 4, 5]

raise NotImplementedError
```


```python
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```


```python

```
