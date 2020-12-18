## GCD & LCM

we know the relation between GCD and LCM is : 
```python
GCD(a,b) × LCM (a,b) = |a×b|
```
But this is not ideal in this kind of question, Because it takes a lot complexity. 
Therefore, the best way is usgin the prime factorization !! 

### Prime Factorization
 
```python
find GCD(6,21) and LCM(6,21) ? 

primeFactors of 6 : 2 × 3 
primeFactors of 21 : 3 × 7 
```
![](/PF1.PNG)
```python
so the 'common factors' is only {3} ==> GCD 
and the all factors are {2, {3}, 7} ==> LCM

So GCD(6,21) = 3, LCM(6,21) = 42
```
Another example :
```python
find GCD(12,20) and LCM(12,20) ? 

primeFactors of 12 : 2 × 2 × 3 
primeFactors of 21 : 2 × 2 × 5 
```
![](/PF2.PNG)
```python
so the 'common factors' is only {2^2} ==> GCD 
and the all factors are {2^2, 3, 7} ==> LCM    # as they are in venn diagram

So GCD(12,20) = 4, LCM(12,20) = 60
```
Now how can we find (a,b) by knowing the GCD and LCM values ?? 
### find (a,b) 







