## GCD & LCM

we know the relation between GCD and LCM in general : 
```python
GCD(a,b) × LCM (a,b) = |a×b|
```
But this is not ideal in this kind of question, Because it takes a lot complexity. 
Therefore, the best way is usgin the prime factorization !! 

### Prime Factorization
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

Another example :
```python
find GCD(300,630) and LCM(300,630) ? 

primeFactors of 300 : 2 × 3 × 5 
primeFactors of 630 : 2 × 3 × 5 × 7 
```
![](/PF3.PNG)
```python
so the 'common factors' {2 × 3 × 5} ==> GCD 
and the all factors are {{2 × 3 × 5} × 2 × 3 × 5 × 7} ==> LCM

So GCD(300,630) = 30, LCM(300,630) = 6300
```
Now how can we find (a,b) by knowing the GCD and LCM values ?? 
### find (a,b) 







