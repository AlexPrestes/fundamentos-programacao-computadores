# Algoritmos da Lista 05
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
matrizA = []
matrizB = []
matrizC = []
m = 0

while m < 4:
    if m < 2:
        matrizA.append([float(i) for i in input().split()])
    else:
        matrizB.append([float(i) for i in input().split()])
    m += 1

for i in range(2):
    matrizC.append([0]*2)

for i in range(2):
    for j in range(2):
        matrizC[i][j] = matrizA[i][j] + matrizB[i][j]

for i in range(2):
    print('%.2f %.2f' % (matrizC[i][0], matrizC[i][1]))
```
### Tarefa 02
```python
m,n = input().split()
m,n = int(m),int(n)
matriz = []
matrizI = []

for i in range(n):
    matrizI.append([0]*m)

for i in range(m):
    matriz.append([float(j) for j in input().split()])

for i in range(m):
    for j in range(n):
        matrizI[j][i] = matriz[i][j]

for i in matrizI:
    print(' '.join(format(j, '.2f') for j in i))
```
### Tarefa 03
```python
m = 2
matriz = []
matriz_inv = []
matriz_id = []
matriz_d = []

for k in range(m):
    matriz.append([float(i) for i in input().split()])


for k in range(2):
    matriz_d.append([])
    matriz_id.append([])
    for i in range(m):
        matriz_d[k].append([0]*m)
        matriz_id[k].append([0]*m)
        for j in range(m):
            matriz_d[k][i][j] = matriz[i][j]
            matriz_id[k][i][i] = 1

a,b,pivo = 0,1,1

for i in range(m):
    for j in range(m):
        for k in range(m):
            if i != j:
                ## Calculo para a determinante
                matriz_d[a][j][k] = ((matriz_d[b][i][i]*matriz_d[b][j][k]) - (matriz_d[b][j][i]*matriz_d[b][i][k]))/pivo
                
                ## Calculo para a matriz inversa
                matriz_id[a][j][k] = ((matriz_d[b][i][i]*matriz_id[b][j][k]) - (matriz_d[b][j][i]*matriz_id[b][i][k]))/pivo
            else:
                matriz_d[a][j][k] = matriz_d[b][j][k]
                matriz_id[a][j][k] = matriz_id[b][j][k]
                
    pivo = matriz_d[b][i][i]
    a,b = b,a

determinante = pivo

if determinante:
    for i in matriz_id[b]:
        matriz_inv.append([(j/determinante) for j in i])
    
    for i in matriz_inv:
        print(' '.join(format(j, '.2f') for j in i))
else:
    print('Singular')
```
### Tarefa 04
```python
m = [int(i) for i in input().split()]

matriz_a = []
matriz_b = []
matriz_c = []

for i in range(m[0]):
    matriz_a.append([float(j) for j in input().split()])

for i in range(m[2]):
    matriz_b.append([float(j) for j in input().split()])

for i in range(m[0]):
    matriz_c.append([0]*m[3])

if m[1] == m[2]:
    for i in range(m[0]):
        for j in range(m[3]):
            matriz_c[i][j] += sum([float(matriz_a[i][k]*matriz_b[k][j]) for k in range(m[1])])

    for i in matriz_c:
        print(' '.join(format(j, '.2f') for j in i))
else:
    print('Incompatíveis')
```
### Tarefa 05
```python
m = int(input())
matriz = []

for i in range(m):
    matriz.append([float(j) for j in input().split()] + [0])
matriz.append([0]*(m+2))

for i in range(m):
    for j in range(m):
        matriz[m][j] += matriz[i][j]
        matriz[i][m] += matriz[i][j]
    
    matriz[m][m] += matriz[i][i]
    matriz[m][m+1] += matriz[i][m-1-i]


numeros = [matriz[m][m+1], matriz[m][m]]

for i in range(m):
    numeros.extend([matriz[m][i],matriz[i][m]])


if not (min(numeros) - max(numeros)):
    print('%d' % min(numeros))
else:
    print('-1')
```
### Tarefa 06
```python
m = [int(i) for i in input().split()]
matriz = [[],[],[]]


matriz[0].append([0]*(m[1]+2))
matriz[1].append([0]*(m[1]+2))

for i in range(m[0]):
    matriz[0].append([0] + [int(j) for j in input().split()] + [0])
    matriz[1].append([0]*(m[1] + 2))
    
matriz[0].append([0]*(m[1]+2))
matriz[1].append([0]*(m[1]+2))

for i in range(1,1+m[0]):
    for j in range(1,1+m[1]):
        if matriz[0][i][j]:
            for k in range(-1,2):
                for l in range(-1,2):
                    if k or l:
                        matriz[1][i+k][j+l] += 1

for i in range(1,m[0]+1):
    matriz[2].append(matriz[1][i][1:m[1]+1])
    for j in range(1,m[1]+1):
        if matriz[0][i][j]: matriz[2][i-1][j-1] = -1

for i in matriz[2]:
    print(' '.join(format(j, 'd') for j in i))
```
### Tarefa 07
```python
matriz = []
encontros_m = [0,0,0,0]

for m in range(8):
    matriz.append([int(i) for i in input().split()])

for j in range(-7,15):
    encontros_u = 0
    encontros_d = 0
    for i in range(8):
        encontros_f = 0
        encontros_b = 0
        if i+j >= 0 and i+j < 8:
            encontros_d += matriz[i][i+j]
        if -i+j >= 0 and -i+j < 8:
            encontros_u += matriz[i][-i+j]
        for k in range(8):
            encontros_f += matriz[i][k]
            encontros_b += matriz[k][i]
            
        if encontros_m[2] < encontros_f: encontros_m[2] = encontros_f
        if encontros_m[3] < encontros_b: encontros_m[3] = encontros_b
        
    if encontros_m[0] < encontros_u: encontros_m[0] = encontros_u
    if encontros_m[1] < encontros_d: encontros_m[1] = encontros_d

if not (max(encontros_m) - 1):
    print('N')
else:
    print('S')
```
### Tarefa 08
```python
m = 3
matriz = []

for i in range(m):
    #matriz.append([float(j) for j in input().split('|')] + [0])
    a = []
    for j in input().split('|'):
        if j == 'X':
            a.append(1)
        else:
            a.append(0)
    matriz.append(a + [0])
            
matriz.append([0]*(m+2))

for i in range(m):
    for j in range(m):
        matriz[m][j] += matriz[i][j]
        matriz[i][m] += matriz[i][j]
    
    matriz[m][m] += matriz[i][i]
    matriz[m][m+1] += matriz[i][m-1-i]


numeros = [matriz[m][m+1], matriz[m][m]]

for i in range(m):
    numeros.extend([matriz[m][i],matriz[i][m]])

if max(numeros) == 3:
    print('X')
elif min(numeros) == 0:
    print('O')
else:
    print('Velha')
```
### Tarefa 09
```python
m = [int(i) for i in input().split()]
matriz = []

for i in range(m[0]):
    matriz.append([int(j) for j in input().split()])

for i in range(m[2]):
    a = [int(j) for j in input().split()]
    if matriz[a[0]][a[1]]: matriz[a[0]][a[1]] += -1

ganhador = 0

for i in matriz:
    ganhador += sum(i)

if not ganhador:
    print('S')
else:
    print('N')
```
### Tarefa 10
```python
m = [int(i) for i in input().split()]
matriz = []
lista = []


for i in range(m[0]):
    matriz.append([int(j) for j in input().split()])

for i in range(m[0]-2):
    for j in range(m[1]-2):
        soma = 0
        for k in range(3):
            for l in range(3):
                if not [k,l] in [[1,0],[1,2]]: soma += matriz[i+k][j+l]
        lista.append(soma)

print(max(lista))
```
