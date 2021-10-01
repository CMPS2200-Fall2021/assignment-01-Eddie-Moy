

# CMPS 2200 Assignment 1

**Name:** Eddie Moy


In this assignment, you will learn more about asymptotic notation, parallelism, functional languages, and algorithmic cost models. As in the recitation, some of your answer will go here and some will go in `main.py`. You are welcome to edit this `assignment-01.md` file directly, or print and fill in by hand. If you do the latter, please scan to a file `assignment-01.pdf` and push to your github repository. 
  
  

1. **Asymptotic notation**

  - 1a. Is $2^{n+1} \in O(2^n)$? Why or why not? 
.  Yes, it is the same as 2^n * 2 and in big O notation we drop any constants.
.  We can add a constant like 3 to 2^n to make it 3 * 2^n.
.  Used Equation grapher to check
.  
. 
  - 1b. Is $2^{2^n} \in O(2^n)$? Why or why not?     
.  No, this function is not O(2^n) because it asymptotically dominates n^2.
.  In other words, it grows at a significantly faster rate than O(2^n)
.  This is shown because no constant c can be added to 2^n to make it grow faster than 2^2^n.
.  Used equation grapher to check
.  
  - 1c. Is $n^{1.01} \in O(\mathrm{log}^2 n)$?    
.  No it does not.
.
.  
.  

  - 1d. Is $n^{1.01} \in \Omega(\mathrm{log}^2 n)$?  
.  Yes 
.  
.  
.  
  - 1e. Is $\sqrt{n} \in O((\mathrm{log} n)^3)$?  
.  Yes 
.  
.  
.  
  - 1f. Is $\sqrt{n} \in \Omega((\mathrm{log} n)^3)$?  
.  No
.  
.  
.  

  - 1g. Consider the definition of "Little o" notation:
  
$g(n) \in o(f(n))$ means that for **every** positive constant $c$, there exists a constant $n_0$ such that $g(n) \le c \cdot f(n)$ for all $n \ge n_0$. There is an analogous definition for "little omega" $\omega(f(n))$. The distinction between $o(f(n))$ and $O(f(n))$ is that the former requires the condition to be met for **every** $c$, not just for some $c$. For example, $10x \in o(x^2)$, but $10x^2 \notin o(x^2)$.  

.  

**Prove** that $o(g(n)) \cap \omega(g(n))$ is the empty set.  

.  Little o means that at some n nought, every single positive constant c makes f(n) larger than g(n). Likewise, the converse is true for little omega.
.  If we make up a made up function, lets call it y(n). And attempt to say that it is part of this set $o(g(n)) \cap \omega(g(n))$. That would mean it would at the
.  same time y(n) in o(g(n) and also y(n) in w(g(n)). This is impossible because there is no such c that can make both statements true.
.  
.  
.  
.  
.  
.  
.  
.  
.  



2. **SPARC to Python**

Consider the following SPARC code:  
$$
\begin{array}{l}
\mathit{foo}~x =   \\
~~~~\texttt{if}{}~~x \le 1~~\texttt{then}{}\\
~~~~~~~~x\\   
~~~~\texttt{else}\\
~~~~~~~~\texttt{let}{}~~(ra, rb) = (\mathit{foo}~(x-1))~~,~~(\mathit{foo}~(x-2))~~\texttt{in}{}\\  
~~~~~~~~~~~~ra + rb\\  
~~~~~~~~\texttt{end}{}.\\
\end{array}
$$ 

  - 2a. Translate this to Python code -- fill in the `def foo` method in `main.py`  

  - 2b. What does this function do, in your own words?  
.  This function takes in an integer n and returns the fibonacci number at index n. 
.  FIbonacci sequence --> 0 1 1 2 3 5 8 13 21 34 55...
.  Foo(8) returns 21
.  
.  
.  
  


3. **Parallelism and recursion**

Consider the following function:  

```python
def longest_run(myarray, key)
   """
    Input:
      `myarray`: a list of ints
      `key`: an int
    Return:
      the longest continuous sequence of `key` in `myarray`
   """
```
E.g., `longest_run([2,12,12,8,12,12,12,0,12,1], 12) == 3`  
 
  - 3a. First, implement an iterative, sequential version of `longest_run` in `main.py`.  

  - 3b. What is the Work and Span of this implementation?  

.  The work is O(n) because everything is looped through only once.
.  The Span is also O(n) because there is nothing that could be parallelized.
.  
.  
.  
.  
.  
.  
.  


  - 3c. Next, implement a `longest_run_recursive`, a recursive, divide and conquer implementation. This is analogous to our implementation of `sum_list_recursive`. To do so, you will need to think about how to combine partial solutions from each recursive call. Make use of the provided class `Result`.   

  - 3d. What is the Work and Span of this sequential algorithm?  
.  The work is still O(n)
.  The Span is still O(n), no parallelization is still possible
.  
.  
.  
.  
.  
.  
.  
.  
.  


  - 3e. Assume that we parallelize in a similar way we did with `sum_list_recursive`. That is, each recursive call spawns a new thread. What is the Work and Span of this algorithm?  

.  The work is O(n)
.  This time the span is O(log(n))
.  
.  
.  
.  
.  
.  

