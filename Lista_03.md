# Algoritmos da Lista 03
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
n = int(input())

for i in range(1,11):
    print(n,'*',i,'=',n*i)
```
### Tarefa 02
```python
s,n = 0,int(input())

for i in range(0,n+1):
    a = 16**((-1)*i)
    b = 4*(8*i+1)**(-1)
    c = 2*(8*i+4)**(-1)
    d = 1*(8*i+5)**(-1)
    e = 1*(8*i+6)**(-1)
    
    s += a*(b-c-d-e)

print('%.48f' % s)
```
### Tarefa 03
```python
n = int(input())
p = 0

for i in range(2,n):
    if not n%i:
        print(i)
        p += 1
        
if not p: print('primo')
```
### Tarefa 04
```python
t = int(input())
n = ((23-5)*60)+56

for i in range(0,n,t):
    h = (i/60) + 5
    m = i%60
    print('%02d:%02d' % (h,m))
```
### Tarefa 05
```python
a,b = input().split()
a,b,s = int(a),int(b),0

if a > b: a,b=b,a

for i in range(a,b+1):
    if i%2: s += i

print(s)
```
### Tarefa 06
```python
n = int(input())
p = 0

for i in range(1,n):
    if not n%i:
        p += i

if p == n:
    print(True)
else:
    print(False)
```
### Tarefa 07
```python
n = int(input())
s=0

for i in range(0,n+1):
    s += i/(n-i+1)

print('%.48f' % s)
```
### Tarefa 08
```python
a,b=input().split()
a,b=int(a),int(b)

mmc = a*b

if a < b:
  a,b = b,a

while (a % b):
    a,b = b,(a%b)

mmc /= b

print(int(mmc))
```
### Tarefa 09
```python
n = int(input())
e = len(str(n))
s = 0

for i in str(n):
    s += int(i)**e

if s==n:
    print(True)
else:
    print(False)
```
### Tarefa 10
```python
x,y,z,r = input().split()
x,y,z,r = int(x),int(y),int(z),int(r)
n = 0

for x1 in range(x-r,x+r+1):
    for y1 in range(y-r,y+r+1):
        for z1 in range(z-r,z+r+1):
              if (x1-x)**2 + (y1-y)**2 + (z1-z)**2 <= r**2:
                  n += 1

print(n)
```
