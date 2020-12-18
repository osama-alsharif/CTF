## Least Greatest

we know the relation between GCD and LCM in general : 
```python
GCD(a,b) × LCM (a,b) = |a×b|
```
But brute forcing is not ideal in this type of question, Because it takes a lot complexity. 

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
Now how can we find (a,b) by knowing the GCD and LCM ?? 
### find the prime factors  
```python
now they alrealy gave as the GCD => common factor.
and we want to get the all other factors !! 
and this done by getting the prime factors of the number that is = LCM(a,b) / GCD(a,b) = A 
then calculate all possible combinations of A = number of pairs   
# from Ex2 : 
# {{2 × 3 × 5} × 2 × 3 × 5 × 7} / {2 × 3 × 5} =  {2 × 3 × 5 × 7}
```
![](/PF5.PNG)
So we gonna write a python3 script that finds all these prime factors, using "sympy.primefactors" module
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
```
![](/PF6.PNG)
So in the end the number of possible pairs = 
![sec-img](https://latex.codecogs.com/gif.latex?2%5E%7Bunique.prime.factors%7D)


## Main Solution 
```python
from sympy import primefactors

GCD = 30
LCM = 6300
Ans = 0

if GCD == LCM:
    Ans = 1
else:
    A = LCM // GCD
    PF = list(primefactors(A))
    Ans = 2**(len(PF))
  
print(Ans)
```

## Socket Connection
```python 
#!/usr/bin/python3
from sympy import primefactors
import socket, time, sys

class NetCat:
	def __init__(self, host="0.0.0.0", port=1337):
		self.CSock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		self.host , self.port = host , port 
		self.LAST_RECV = '' 
		
		self.CSock.connect((self.host, self.port))

		self.LAST_RECV = self._Recv_(self.CSock)
		print(self.LAST_RECV)


	def _Send_(self, data, CSock, NewLine=True):
		CSock.sendall((str(data).rstrip('\n') + ('\n' if NewLine else '')).encode()) # +- '\n' 
		time.sleep(0.5)


	def _Recv_(self, CSock):
		return CSock.recv(16384).decode('utf-8').rstrip('\n')

	def Handle(self):
		while True:
			print(self.LAST_RECV)

			context = self.LAST_RECV.split('\n')

			if context[-1] == '':
				context.pop()

			# question dependencies ######################  

			GCD = int(context[-2].split('=')[-1].strip(' '))
			LCM = int(context[-1].split('=')[-1].strip(' '))
			
			ans = 0
			if GCD == LCM:
				ans = 1
			elif LCM % GCD == 0:
				A = LCM // GCD
				PF = list(primefactors(A))
				ans = 2**len(PF)
			
			print(ans)
			self._Send_(ans, self.CSock) 
			self.LAST_RECV = self._Recv_(self.CSock)

			# question dependencies ###################### 

		self.CSock.close()		

	def Close(self):
		print('Iam oout ^^')
		self.CSock.close()


def main():
	Host, Port = "challs.xmas.htsp.ro", 6050

	Client = NetCat(Host, Port)
	try:
		Client.Handle()
	except: 
		server.Close()
	finally:
		Client.Close()			

if __name__ == "__main__":
	main()
```







