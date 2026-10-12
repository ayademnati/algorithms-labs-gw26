# CSCI 3212 Lab 1

## Fibonacci numbers

Source: https://en.wikipedia.org/wiki/Fibonacci_sequence  

The Fibonacci sequence is a sequence of numbers where:  
1. The first and second numbers are both ``1``, that is, ``fibonacci(1) = fibonacci(2) = 1``
2. The numbers that follow are the sum of the previous TWO numbers, so  
``fibonacci(3) = fibonacci(2) + fibonacci(1) = 1 + 1 = 2``  
``fibonacci(4) = fibonacci(3) + fibonacci(2) = 2 + 1 = 3``.

```
TODO: Answer the following questions:
fibonacci(5) = fibonacci(4) + fibonacci(3) = 3 + 2 = 5
fibonacci(6) = fibonacci(5) + fibonacci(4) = 5 + 3 = 8
fibonacci(7) = fibonacci(6) + fibonacci(5) = 8 + 5 = 13
fibonacci(8) = fibonacci(7) + fibonacci(6) = 13 + 8 = 21
fibonacci(9) = fibonacci(8) + fibonacci(7) = 21 + 13 = 34
```

## Basic implementation

Let's take a look at an implementation:
```python
def fibonacci(n):
    if n <= 0:
        return 0
    if n == 1:
        return 1
    return fibonacci(n-1) + fibonacci(n-2)
```
You can also find this in ``algorithms-labs-gw26/lab1/fibonacci.py``, and run it: 
```bash
cd algorithms-labs-gw26/lab1
python fibonacci.py
```
The code version also tells you how much time does it take to complete each calculation.
```
TODO:
1. Explain what the code above is doing.
A: solves fibonacci recursively. The first two if statements are base cases, and the return statement is the recursive call for when n is not <= 0 or = 1.
2. What happens if we remove the "if ... return ..." and only keep the last line?
A: infinite calls because we would have no base cases to return from, the function would just keep calling itself infinitely.
3. What is fibonacci(20)? how much time did it take to calculate that?
A: 6765
4. What is fibonacci(30)? how much time did it take to calculate that?
A: 832040
5. How much time did it take you to calculate fibonacci(40)? (this might take a while...)
A: 102334155
```

## How many function calls?

Modify ``fibonacci_counting.py`` so that it does the same calculation as ``fibonacci.py``, but it also counts how many times the function ``fibonacci(n)`` had to be called. Then answer the following:
```
TODO:
1. How many function calls does fibonacci(1) take? 1 
2. How many function calls does fibonacci(5) take? 15
3. How many function calls does fibonacci(10) take? 177
4. Why is it so slow? Where does the complexity come from? because there are so many subproblems, each subproblem has many subproblems, and you have to backtrack all of the subproblems.
5. Is this O(n)? is this O(2^n)? Why? O(2^n) because for every recursive call, it calls two more recursive calls (i.e. the subproblems).
6. Is this Ω(n)? Why? in the best case, it runs in linear time.
```

## Memoization Optimization

Take a look at ``fibonacci_counting.py``, where memoization is used.
```
TODO:
1. How is this one different from the previous one? it checks a memory cache before doing any recursive calls.
2. How much time does it take to calculate fibonacci(30)? O(n)
3. Why is it often faster? because if we already calculated a fibonacci of some n it is stored, so that we don't have to keep recalculating it.
4. Also modify this file to count: how many times the function had to be called for fibonacci(30)? 30
5. Is this O(n)? is this O(2^n)? Why? O(n), because each fibonacci is calculated once.
6. Is this Ω(n)? is this Ω(2^n)? Why? Ω(n), because it is the best case
```

## Extension: Staircase Problem

Implement ``fibonacci_threeway.py``, where:
1. The first, second, and third numbers are ``1``.
2. The numbers afterwards are the sum of the previous **THREE** numbers, instead of two.
3. Your implementation should be optimized, taking less than 1 second to calculate ``fibonacci_threeway(50)``.

## Optional, challenge problems
1. Instead of recursion, implement ``fibonacci(n)`` using iteration instead.
2. ``fibonacci_memoized.py`` fails if you give it a very large input number such as one million - why? Try fixing it.
3. There is an even faster way to calculate fibonacci numbers, in (almost) O(1) time. Read Wikipedia and try to implement it, or if you like a big challenge, implement it without looking it up.