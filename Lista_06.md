# Algoritmos da Lista 06
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
comando = eval(input())
agenda = {}

while comando[0] != 'Encerrar':
    if comando[0][0:7] == 'Inserir':
        if comando[1] not in agenda: agenda[comando[1]] = []
        if comando[0][7:] == 'Telefone': agenda[comando[1]].append(comando[2])
    else:
        if comando[0][7:] == 'Pessoa' and comando[1] in agenda:
            del agenda[comando[1]]
        else:
            if comando[1] in agenda and comando[2] in agenda[comando[1]]:
                agenda[comando[1]].remove(comando[2])

    comando = eval(input())

print(agenda)
```
### Tarefa 02
```python
trin_rna = input()
traducao = []

dictionary = {'UUU':'Phe','CUU':'Leu','UUA':'Leu','AAG':'Lis','UCU':'Ser','UAU':'Tyr','CAA':'Gln'}

for i in range(0,len(trin_rna),3):
    traducao.append(dictionary[trin_rna[i:i+3]])

print('-'.join(traducao))
```
### Tarefa 03
```python
trajeto = eval(input())

rotas = {}

while ( len(trajeto) - 1 ):
    if trajeto[1] not in rotas.get(trajeto[0],[]):
        rotas[trajeto[0]] = rotas.get(trajeto[0],[]) + [trajeto[1]]
    trajeto = eval(input())

for origem, destinos in list(rotas.items()):
    for destino in destinos:
        if origem in rotas.get(destino,[]) and destino in rotas.get(origem,[]):
            if origem in rotas.get(destino,[]): rotas[destino].remove(origem)
            if destino in rotas.get(origem,[]): rotas[origem].remove(destino)
    if not rotas.get(origem,[]): del rotas[origem]

print(rotas)
```
### Tarefa 04
```python
numero = {'2':2, '3':3, '4':4, '5':5, '6':6, '7':7, '8':8, '9':9, '10':10, 'J':11, 'Q':12, 'K':13, 'A':14}
naipe = {'ouros':100, 'espadas':200, 'copas':300, 'paus':400}

jogador_1 = input().split()
jogador_2 = input().split()

numero_jogadas = int(len(jogador_1)/2)

vitorias = [0,0,0]

for i in range(numero_jogadas):

    numero_carta_1 = naipe[ jogador_1[i*2 + 1] ] + numero[ jogador_1[i*2] ]
    numero_carta_2 = naipe[ jogador_2[i*2 + 1] ] + numero[ jogador_2[i*2] ]

    if numero_carta_1 > numero_carta_2: vitorias[1] += 1
    if numero_carta_1 < numero_carta_2: vitorias[2] += 1

if vitorias[1] != vitorias[2]:
    print(vitorias.index(max(vitorias)))
else:
    print('0')
```
### Tarefa 05
```python
frase = input().lower().split()
frase_dic = {}

for v in range(len(frase)):
    k = frase[v].strip('.').strip(',')
    frase_dic[k] = frase_dic.get(k,[]) + [str(v+1)]

for i in range(int(input())):
    palavra = input().lower()
    print(' '.join(frase_dic.get(palavra,'-')))
```
### Tarefa 06
```python
alfa_normal = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ'
alfa_encript = input()
alfa_descript = {}

alfa_descript = dict([ [alfa_encript[i], alfa_normal[i]] for i in range(26) ])

frase_encript = input().split()

frase_descript = ''

for palavra in frase_encript:
    for letra in palavra:
        frase_descript += alfa_descript.get(letra,letra)
    frase_descript += ' '

print(frase_descript)
```
### Tarefa 07
```python
texto = input().lower()

conta_frase = texto.count('.') + texto.count('?') + texto.count('!')
conta_palavras = {}

contagem = [0,0,conta_frase]

for palavra in texto.split():
    for simbolo in palavra:
        if not simbolo.isalpha():
            palavra = palavra.strip(simbolo)
    
    conta_palavras[palavra] = conta_palavras.get(palavra,0) + 1

for i in list(conta_palavras.values()):
    if i > 1: contagem[1] += i - 1
    contagem[0] += 1

print(' '.join( [ str(i) for i in contagem ] ))
```
