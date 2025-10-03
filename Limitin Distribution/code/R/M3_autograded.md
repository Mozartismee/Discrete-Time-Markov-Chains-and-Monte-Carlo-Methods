# Summary Assignment for Module 3
<blockquote>This is an assignment in a Jupyter notebook which will be autograded. (It is not a programming assignment but rather is using tools from a Jupyter notebook that allows for calculations and more free-form answers than the other kinds of assignments you have seen so far in this course.) To avoid autograder errors, please do not add or delete any cells. Also, run all cells even if they are hidden and not requiring any input from you. You may add additional calulations or print statements to any cell to help you see the current values of variables you may be working with. 
</blockquote>

**Rounding Error:** Ideally, your answers will be given from a direct R calculation. For example, given a matrix $A$, if you are asked to multiply the $(1,3)$ entry with the $(2,2)$ entry and to store the result in a variable `x`, you would type

<code>x = A[1,3]*A[2,2]</code>

However, if you compute `A[1,3]*A[2,2]` and see `0.23719445178`, you could choose to type out the answer as, for example,

<code>x = 0.23719445</code>

<u>as long as you keep at least 3 decimal places of accuracy</u>.


```R
# Load Necesary Libraries for Autograding
library(testthat)
```


```R
# Run this cell. It is necessary for autograding. It will also allow you to take powers of a matrix using
# "%^%" if you choose.
# Note that this cell may take a few moments to run. Do not proceed further until you see a response with a red 
# background below this cell or until "In[]" or "In[*]" to the left of the cell has a number in the brackets
library("expm")
```

    Loading required package: Matrix
    
    
    Attaching package: ‘expm’
    
    
    The following object is masked from ‘package:Matrix’:
    
        expm
    
    


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


```R
# Run this cell. Consider adding a "P" as the last line in the cell
# if you would like to see the matrix more clearly
P = matrix(0,6,6)
P[1,] = c(0.4,0,0,0.5,0,0.1)
P[2,] = c(0,0.8,0,0,0.2,0)
P[3,] = c(0,0,0.3,0.5,0.2,0)
P[4,] = c(0.9,0,0,0.1,0,0)
P[5,] = c(0,0.5,0,0,0.5,0)
P[6,] = c(0,0,0,1,0,0)
```

**Part A)** How many communication classes does this Markov chain have?

Save your answer as p1.a.


```R
p1.a = NA

# your code here
p1.a = 3
.NotYetImplemented()
```


    Error: '.NotYetImplemented' is not implemented yet
    Traceback:


    1. .NotYetImplemented()

    2. stop(gettextf("'%s' is not implemented yet", as.character(sys.call(sys.parent())[[1L]])), 
     .     call. = FALSE)



```R
# Hidden Test Cell
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
    


```R
classes = matrix(0,p1.a,6)
# your code here
classes = matrix(
  c(
    1,4,6,0,0,0,   # {1,4,6}
    2,5,0,0,0,0,   # {2,5}
    3,0,0,0,0,0    # {3}
  ),
  nrow = p1.a, byrow = TRUE
)

.NotYetImplemented()
```


    Error in matrix(0, p1.a, 6): invalid 'nrow' value (too large or NA)
    Traceback:


    1. matrix(0, p1.a, 6)



```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part C)** Find the period for each state.

Save your answer as a vector called <code>p1.c</code> of length $6$, containing the period of states $1$, $2$, $3$, $4$, $5$, and $6$, respectively.


```R
p1.c = NA
# your code here
# 都有自回邊（除了 6，但 6 與有自回邊的 1,4 同類，所以也為 1）
p1.c = c(1,1,1,1,1,1)

.NotYetImplemented()
```


    Error: '.NotYetImplemented' is not implemented yet
    Traceback:


    1. .NotYetImplemented()

    2. stop(gettextf("'%s' is not implemented yet", as.character(sys.call(sys.parent())[[1L]])), 
     .     call. = FALSE)



```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part D)** Starting from state $3$, what is the approximate probability that this Markov chain ends up in states $1$, $2$, $3$, $4$, $5$, or $6$, in the long-run?

Use the next cell to inspect high powers of the transition probability matrix until your answers are stable to three decimal places. Then move to the following cell to save your answer as a vector p1.d of length $6$, containing the observed long-run probability  states $1$, $2$, $3$, $4$, $5$, and $6$, respectively.


```R
# Use this cell to take some high powers of the transition probability matrix P.

```


```R
p1.d = NA
# your code here
# 這是穩定到 3 位小數的數值
p1.d = c(0.404313, 0.204082, 0.000000, 0.269542, 0.081633, 0.040431)

.NotYetImplemented()
```


    Error: '.NotYetImplemented' is not implemented yet
    Traceback:


    1. .NotYetImplemented()

    2. stop(gettextf("'%s' is not implemented yet", as.character(sys.call(sys.parent())[[1L]])), 
     .     call. = FALSE)



```R
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


```R
# Run this cell. Consider adding a "P" as the last line in the cell
# if you would like to see the matrix more clearly
P = matrix(0,5,5)
P[1,] = c(0.4,0.2,0.3,0.1,0)
P[2,] = c(0.1,0.3,0.3,0.2,0.1)
P[3,] = c(0.3,0.3,0.2,0.2,0)
P[4,] = c(0.1,0.2,0.2,0.4,0.1)
P[5,] = c(0.9,0,0,0,0.1)
```

**Part A)** Is this chain irreducible? Aperiodic? Recurrent? Positive recurrent? 

Your answers should be in the form <code>TRUE</code> or <code>FALSE</code>. Capitalization matters when defining boolean variables in R. Record your answers as <code>p2.a.irreducible</code>, <code>p2.a.aperiodic</code>, <code>p2.a.recurrent</code>, and <code>p2.a.posrecurrent</code>.


```R
p2.a.irreducible = NA
p2.a.aperiodic = NA
p2.a.recurrent = NA
p2.a.posrecurrent = NA
# your code here
p2.a.irreducible  <- TRUE
p2.a.aperiodic    <- TRUE
p2.a.recurrent    <- TRUE
p2.a.posrecurrent <- TRUE
.NotYetImplemented()

```


```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part B)** Find the long-run proportion of days there will be falling kittens. 

Save your answer as p2.b.
(Reminder: Give all answers to at least 3 decimal places.)


```R
p2.b = NA
# your code here
p2.b <- 0.049
.NotYetImplemented()
```


```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part C)** Find the long-run proportion of days there will be falling kittens followed by a Sunny day. 

Save your answer as p2.c.


```R
p2.c = NA
# your code here
p2.c <- 0.044 
.NotYetImplemented()
```


```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```

**Part D)** What is the most likely state to find this chain in in the long-run? The next most likely? The least likely?

Define a vector-valued variable <code>p2.d</code> of length $5$ that gives the corresponding rankings for states $1$ through $5$, respectively. For example, if "Sunny" is the third most likely state, the first value of p2.d should be $3$. As always in the notebooks for this course, it is fine to observe what is going on and to fill out the vector "by hand" rather than coding something that will give these rankings.



```R
# This is a free cell for you to experiment in.

```


```R
p2.d = NA
# your code here
p2.d <- c(1, 3, 2, 4, 5)
.NotYetImplemented()
```


```R
# Hidden Test Cell
# NOTE: This cell contains hidden tests. You will not see whether you passed these tests until you submit your assignment.
# Any cell labeled "Hidden Test Cell" MAY have hidden tests.
```


```R

```
