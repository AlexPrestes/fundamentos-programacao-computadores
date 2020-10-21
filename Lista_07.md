# Algoritmos da Lista 07
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
lista = [ float(i) for i in input().split() ]
print(' '.join([ '%.2f' % i for i in lista ]))

for i in range( 1, len(lista) ):
    chave = lista[i]

    while i > 0 and chave > lista[i-1]:
        lista[i-1], lista[i] = lista[i], lista[i-1]
        i -= 1

    print(' '.join([ '%.2f' % i for i in lista ]))
```
### Tarefa 02
```python
entradas = [ int(i) for i in input().split() ]

a, b = 1, entradas[0]
conta_teste = 1

while a < b-1: 
    m = (a + b) // 2

    if m > entradas[1]: b = m
    else: a = m

    conta_teste += 1

print(conta_teste)
```
### Tarefa 03
```python
tabela = {}

for i in range(int(input())):
    partida = eval(input())
    if partida[1] < partida[2]:
        pontos = [0,3]
    elif partida[1] > partida[2]:
        pontos = [3,0]
    else:
        pontos = [1,1]

    tabela[partida[0]] = tabela.get(partida[0],0) + pontos[0]
    tabela[partida[3]] = tabela.get(partida[3],0) + pontos[1]

tabelas_lista = sorted([ [valor,chave] for chave,valor in list(tabela.items()) ], reverse=True)

for chave,valor in tabelas_lista:
    print(valor)
```
### Tarefa 04
```python
a,b,c = [ float(i) for i in input().split() ]
l,r = [ float(i) for i in input().split() ]
k = 'INDETERMINADO'
intervalo = False

fl = a*l**2 + b*l + c
fr = a*r**2 + b*r + c

condicao_cres = (a*l**2 + b*l + c < 0 and a*r**2 + b*r + c > 0)
condicao_desc = (a*l**2 + b*l + c > 0 and a*r**2 + b*r + c < 0)

if condicao_desc: l,r=r,l

if condicao_cres or condicao_desc: intervalo = True

while intervalo and not (abs(l - r) < 1e-8):
    m = (l + r) / 2

    if (a*(m**2)) + (b*m) + c > 0:
        r = m
    else:
        l = m

    k = '%.8f' % l

print('%s' % k)
```
