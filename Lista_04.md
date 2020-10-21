# Algoritmos da Lista 04
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
vetor = [int(i) for i in input().split()]

soma = 0
ocorren = 0
maior = 0
posicao = ''
j = 0

for i in range(len(vetor)):
    soma += vetor[i]
    if vetor[i] == 9: ocorren += 1
    if vetor[i] > maior:
        maior = vetor[i]

for i in range(len(vetor)):
    if maior == vetor[i]:
        posicao += str(i) + ' '
    
    
print('%d\n%d\n%d\n%s' % (soma, ocorren, maior, posicao))
```
### Tarefa 02
```python
vetor = [i for i in input().split()]

n_vetor = []

for i in range(-1,len(vetor) - 1):
    n_vetor.append(vetor[i])

' '.join(n_vetor)

print(' '.join(n_vetor))
```
### Tarefa 03
```python
vetor = [i for i in input().split()]

print(' '.join(vetor[-1::-1]))
```
### Tarefa 04
```python
maior_5 = 0
par = 0
impar = 0
cont = 0
lista = ''

v = int(input())

while v >= 0:
    if v > 5: maior_5 += 1
    if not v%2: par += v
    if v%2: impar += v
    cont += 1
    lista += str(v) + ' '
    
    v = int(input())

print('%s\n%s\n%s\n%s\n%s' % (maior_5,par,impar,cont,lista))
```
### Tarefa 05
```python
vetor = [[float(i) for i in input().split()]]

for j in range(1,int(vetor[0][2]) + 1):
    vetor.append([float(i) for i in input().split()])

for j in range(1,int(vetor[0][2]) + 1):
      for k in range(int(vetor[0][1])):
          vetor[j][0] = ((vetor[0][0]*vetor[j][3]) + vetor[j][0])
          vetor[j][1] = ((vetor[0][0]*vetor[j][4]) + vetor[j][1])
          vetor[j][2] = ((vetor[0][0]*vetor[j][5]) + vetor[j][2])

for j in range(1,int(vetor[0][2] + 1)):
    print('%.2f %.2f %.2f' % 
    (vetor[j][0]
    ,vetor[j][1]
    ,vetor[j][2]))
```
### Tarefa 06
```python
vetor = [float(i) for i in input().split()]
soma = 0
multi = 1

for i in vetor:
    soma += i
    multi *= i
    print('%.2f %.2f' % (soma,multi))
```
### Tarefa 07
```python
vet = [int(i) for i in input().split()]
pos = []
semdup = []


for i in vet:
    if i >= 0:
        if not pos.count(i):
            semdup.append(i)
        pos.append(i)

print(' '.join([str(i) for i in semdup]))
```
### Tarefa 08
```python
vetor = [float(i) for i in input().split()]
vetor.sort()

desvio = 0

media = sum(vetor)/len(vetor)

if not len(vetor)%2:
    mediana = (vetor[int(len(vetor)/2)] + vetor[int(len(vetor)/2 - 1)])/2
else:
    mediana = (vetor[int(len(vetor)/2)])

for i in vetor:
    desvio += (i - media)**2

desvio = (desvio/len(vetor))**(1/2)

print('%.2f %.2f %.2f' % (media, mediana, desvio))
```
### Tarefa 09
```python
vetor = [int(i) for i in input().split()]

vetor.sort()

n_vetor = []

for i in vetor:
    if (vetor.count(i) - 1) and not (n_vetor.count([str(i),str(vetor.count(i))])):
        n_vetor.append([str(i),str(vetor.count(i))])

for i in n_vetor:
    print(' '.join(i))
```
### Tarefa 10
```python
vlista = []
plista = []
z = []

# Organiza as coordenadas dos vertices do poligono em vlista
j,k = 0,0
for i in input().split():
    if not j%2:
        vlista += [[float(i),0]]
    else:
        vlista[k][1] = float(i)
        k += 1
    j += 1

# Zera os indices
j,k = 0,0

# Organiza as coordenadas dos pontos em plista
for i in input().split():
    if not j%2:
        plista += [[float(i),0]]
    else:
        plista[k][1] = float(i)
        k += 1
    j += 1

# Cria uma matriz da quantidade de pontos por quantidade de vertices
for i in range(len(plista)):
    z.append([0]*(len(vlista)))

# Calcula o produto vetorial entre v e p
for i in range(-1,len(vlista)-1):
	# Calcula o vetor v, diferença do vertice(i + 1) e vertice(i), gerando um vetor que segue o sentido anti-horario
    v=[vlista[i+1][0]-vlista[i][0],vlista[i+1][1]-vlista[i][1]] 
    for j in range(-1,len(plista)-1):
		# Calcula o vetor p, diferença do vertice(i) e ponto(j), gerando um vetor que segue o sentido ponto -> vertice(i)
        p=[vlista[i][0]-plista[j][0],vlista[i][1]-plista[j][1]]
		# Produto vetorial dos vetores v e p, e armazena na matriz z nas posições corretas
        z[j][i]=(v[0]*p[1] - v[1]*p[0])*(-1)

# corre a matriz z, linha a linha
for i in z:
	# Verifica qual o menor valor na linha, caso menor que zero, o ponto está fora do poligono
    if min(i) < 0:
        print('N')
    else:
        print('S')
```
