# Algoritmos da Lista 02
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
a,b,c= input().split()
a,b,c= float(a), float(b), float(c)
d= b**2-4*a*c
if(d<0):
  print("No real roots.")
else:
  x1= (-b+d**(1/2))/(2*a)
  x2= (-b-d**(1/2))/(2*a)
  if(x1==x2):
    print("%.2f"% x1)
  else:
    print("%.2f"%x1)
    print("%.2f"%x2)
```
### Tarefa 02
```python
n= int(input())
if(n%2):
  print("Impar")
else:
  print("Par")
if(n<0):
  print("Negativo")
elif(n==0):
  print("Zero")
else:
  print("Positivo")
```
### Tarefa 03
```python
a,b,c,d,e = input().split()
a,b,c,d,e = float(a),float(b),float(c),float(d),float(e)
if(a>b and a>c and a>d and a>e):
  mx=a
elif(b>a and b>c and b>d and b>e):
  mx=b
elif(c>a and c>b and c>d and c>e):
  mx=c
elif(d>a and d>b and d>c and d>e):
  mx=d
else:
  mx=e
if(a<b and a<c and a<d and a<e):
  mn=a
elif(b<a and b<c and b<d and b<e):
  mn=b
elif(c<a and c<b and c<d and c<e):
  mn=c
elif(d<a and d<b and d<c and d<e):
  mn=d
else:
  mn=e
print("%.2f %.2f"% (mx,mn))
```
### Tarefa 04
```python
x1,y1= input().split()
x2,y2= input().split()
x3,y3= input().split()
x1,x2,x3,y1,y2,y3= float(x1), float(x2), float(x3), float(y1), float(y2), float(y3)
a= ((x2-x1)**2+(y2-y1)**2)**(1/2)
b= ((x3-x1)**2+(y3-y1)**2)**(1/2)
c= ((x3-x2)**2+(y3-y2)**2)**(1/2)
if(a<b+c and b<c+a and c<b+a):
  print("triângulo")
else:
  print("não triângulo")
if(a==b==c):
  print("equilátero")
elif(a==b or b==c or a==c):
  print("isósceles")
else:
  print("escaleno")
```
### Tarefa 05
```python
d,m = input().split('/')
d,m = int(d), int(m)
if(m>=1):
  a=d
if(m>=2):
  a+=31
if(m>=3):
  a+=28
if(m>=4):
  a+=31
if(m>=5):
  a+=30
if(m>=6):
  a+=31
if(m>=7):
  a+=30
if(m>=8):
  a+=31
if(m>=9):
  a+=31
if(m>=10):
  a+=30
if(m>=11):
  a+=31
if(m>=12):
  a+=30
  
  

if (a<19):
    print("Sagitário")
elif(a<46):
    print("Capricórnio")
elif(a<70):
    print("Aquário")
elif(a<108):
    print("Peixes")
elif(a<134):
    print("Áries")
elif(a<171):
    print("Touro")
elif(a<202):
    print("Gêmeos")
elif(a<222):
    print("Câncer")
elif(a<259):
    print("Leão")
elif(a<304):
    print("Virgem")
elif(a<327):
    print("Libra")
elif(a<334):
    print("Escorpião")
elif(a<352):
    print("Serpentário")
else:
    print("Sagitário")
```
### Tarefa 06
```python
a,b,c= input().split()
d= a+c+b
print("%.2f"% eval(d))
```
### Tarefa 07
```python
import math
l= float(input())
t= 2*math.pi*((l/9.8)**(1/2))
print("%.2f"% t)
```
### Tarefa 08
```python
x1,y1,z1= input().split()
x2,y2,z2= input().split()
x1,x2,y1,y2,z1,z2= float(x1), float(x2), float(y1), float(y2), float(z1), float(z2)
l1= abs(x2-x1)+abs(y2-y1)+abs(z2-z1)
l2= ((x2-x1)**2+(y2-y1)**2+(z2-z1)**2)**(1/2)
print("%.2f %.2f"% (l1,l2))
```
### Tarefa 09
```python
a= int(input())
if(a%4):
  print("comum")
else:
  print("bissexto")
```
### Tarefa 10
```python
import math
AB= float(input())
BC= float(input())
H= (((AB**2)+(BC**2))**(1/2))
theta= math.asin(AB/(H))
print(round(math.degrees(theta)))
```
