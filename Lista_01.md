# Algoritmos da Lista 01
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
a = int(input())
if a >= 1000 and a < 10000 :
       a=str(a)
       print(a[-1::-1])
```
### Tarefa 02
```python
a,b,c,d= input().lower().split("a")
print(a+"A"+b+"A"+c+"A"+d)
```
### Tarefa 03
```python
a,b,c= input().split("x")
i,j = a.split("y")
print("x" + j + "y" + b + "y" + c)
```
### Tarefa 04
```python
a,b,c= input().split()
d,e,f= input().split()
a,b,c,d,e,f= float(a), float(b), float(c), float(d), float(e), float(f)
xs, ys, zs= a+d, b+e, c+f 
escalar= (a*d)+(b*e)+(c*f)
xc,yc,zc= (b*f-e*c), -(a*f-d*c), (a*e-d*b)
print("%.2f %.2f %.2f" % (xs, ys, zs))
print("%.2f" % escalar)
print("%.2f %.2f %.2f" % (xc, yc, zc))
```
### Tarefa 05
```python
f= float(input())
c= 5/9*(f-32)
print("%.2f"%c)
```
### Tarefa 06
```python
produto= input()
quantidade= float(input())
valor= float(input())
desconto= float(input())
total= (100-desconto)*valor*quantidade/100
print(produto+": R$ %.2f" % total)
```
### Tarefa 07
```python
a,b,c= input().split(":")
a,b,c= int(a), int(b), int(c)
print(a*3600+b*60+c)
```
### Tarefa 08
```python
t= float(input())
d= 0.34*t
print("%.2f"%d)
```
### Tarefa 09
```python
a,t= input().split()
a,t= float(a), float(t)
d= a*t**2/2
print("%.2f"%d)
```
### Tarefa 10
```python
v,d= input().split()
v,d= float(v), float(d)
a= (v**2)/(2*d)
t= v/a
print("%.2f %.2f"% (a,t))
```
