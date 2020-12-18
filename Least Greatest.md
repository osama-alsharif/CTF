## GCD & LCM

we know the relation between GCD and LCM in general : 
```python
GCD(a,b) × LCM (a,b) = |a×b|
```
But this is not ideal in this kind of question, Because it takes a lot complexity. 
Therefore, the best way is usgin the prime factorization !! 

### Prime Factorization
Ex1 : 
 ```python
find GCD(12,20) and LCM(12,20) ? 

primeFactors of 12 : 2 × 2 × 3 
primeFactors of 21 : 2 × 2 × 5 
```
![](/PF2.PNG)
```python
so the 'common factors' is only {2^2} ==> GCD 
and the all factors are {{2^2} × 3 × 5} ==> LCM      # as they are in venn diagram

So GCD(12,20) = 4, LCM(12,20) = 60
```

Ex2 :
```python
find GCD(300,630) and LCM(300,630) ? 

primeFactors of 300 : 2 × 3 × 5 
primeFactors of 630 : 2 × 3 × 5 × 7 
```
![](/PF4.PNG)
```python
so the 'common factors' {2 × 3 × 5} ==> GCD 
and the all factors are {{2 × 3 × 5} × 2 × 3 × 5 × 7} ==> LCM

So GCD(300,630) = 30, LCM(300,630) = 6300
```
Now how can we find (a,b) by knowing the GCD and LCM values ?? 
### find the prime factors  
```python
now they alrealy gave as the GCD => common factor.
and we want to get the all other factors !! 
and this done by getting the prime factors of the number that is = LCM(a,b) / GCD(a,b) = A 
then calculate all possible combinations of A = number of pairs   
# from Ex2 : 
# {{2 × 3 × 5} × 2 × 3 × 5 × 7} / {2 × 3 × 5} =  {2 × 3 × 5 × 7}
```
So we gonna write a python3 script that finds all these prime factors, 
I used "sympy.primefactors" module
```python
from sympy import primefactors

GCD = 30
LCM = 6300
A = LCM // GCD
PF = list(primefactors(A))  # [2, 3, 5, 7]
```

### find number of pairs (a,b)
note !! (a,b) != (b,a)
the number of pairs = the sum of all combinations of all lengths + 1

![first-img](https://latex.codecogs.com/gif.latex?1%20&plus;%20%5Csum_%7Bk%3D1%7D%5E%7Bn%7D%20%5Cbinom%7Bn%7D%7Bk%7D%3D%202%5E%7Bn%7D)

```python
compinations of {2, 3, 5, 7}
{1}, {2}, {3}, {5}, {7}, {2,3}, {2,5}, {2,7}, {3,5}, {3,7}, {5,7}, {2,3,5}, {2,3,7}, {2,5,7}, {3,5,7}, {2,3,5,7}

now the set and it's complement gives us a possible pair   # ex: (2, 3×5×7)   or  (2 × 5, 3 × 7) .... 

So in the end the number of possible pairs = 
![sec-img](https://latex.codecogs.com/gif.latex?2%5E%7Bn%7D)
```





