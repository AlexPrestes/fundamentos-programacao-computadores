# Algoritmos da Lista 09
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
def arquivo_matriz(nomearquivo):
    matriz = []
    arq = open(nomearquivo)
    
    ordem = []
    
    for linha in arq:
        
        if not ordem:
            ordem = [ int(i) for i in linha.split() ]
        else:
            matriz.append([ float(i) for i in linha.split() ])
    
    arq.close()
    
    return ordem, matriz

def Multiplica_MatrizAB(OrdA, MatrizA, OrdB, MatrizB):
    MatrizC = []
    for i in range(OrdA[0]):
        MatrizC.append([0]*OrdB[1])
    
    for i in range(OrdA[0]):
        for j in range(OrdB[1]):
            MatrizC[i][j] += sum([float(MatrizA[i][k]*MatrizB[k][j]) for k in range(OrdA[1])])

    return [[OrdA[0],OrdB[1]]] + MatrizC

def lista_arquivo(nomearquivo, lista):
    
    arq = open(nomearquivo, 'w')
    arq.write(' '.join([ '%d' % j for j in lista[0] ]))
    arq.write('\n')
    
    for linha in lista[1:]:
        arq.write(' '.join([ '%.2f' % j for j in linha ]))
        arq.write('\n')
        
    arq.close()

def mult_matrizes(A, B, C):
    
    TamA, MatA = arquivo_matriz(A)
    TamB, MatB = arquivo_matriz(B)
    
    if TamA[1] == TamB[0]:
        SaidaMatrizC = Multiplica_MatrizAB(TamA, MatA, TamB, MatB)
        lista_arquivo(C, SaidaMatrizC)
    else:
        arqC = open(C,'w')
        arqC.write('Incompatíveis')
        arqC.close()
```
### Tarefa 02
```python
def arquivo_matriz(nomearquivo):
    matriz = []
    arq = open(nomearquivo)
    
    for linha in arq:
        matriz.append(linha.replace('\n',''))
    arq.close()
    
    return matriz

def lista_arquivo(nomearquivo, lista):
    arq = open(nomearquivo, 'w')
    
    for linha in lista:
        arq.write(linha)
        
    arq.close()

def concat_horizontal(A, B, C, separador):
    
    MatrizA = arquivo_matriz(A)
    MatrizB = arquivo_matriz(B)
    MatrizC = []
    
    
    a = len(MatrizA)
    b = len(MatrizB)
    c = a
    
    if a < b: c = b
    
    for i in range(c):
        linha = []
        if i <= a-1: linha.append(MatrizA[i])
        if i <= b-1: linha.append(MatrizB[i])
        linha[-1] = linha[-1] + '\n'
        MatrizC.append( separador.join(linha) )
        
    lista_arquivo(C, MatrizC)
```
### Tarefa 03
```python
def arquivo_matriz(nomearquivo):
    matriz = []
    arq = open(nomearquivo)
    
    for linha in arq:
        linha = int(linha.replace('\n',''))
        if linha not in matriz: matriz.append(linha)
    arq.close()
    
    matriz.sort()
    
    return matriz

def lista_arquivo(nomearquivo, lista):
    arq = open(nomearquivo, 'w')
    
    for linha in lista:
        arq.write(linha)
        
    arq.close()

def sobrepostos(A, B, C):
    
    MatrizA = arquivo_matriz(A)
    MatrizB = arquivo_matriz(B)
    MatrizC = []
    
    a = len(MatrizA)
    b = len(MatrizB)
    
    for item in MatrizA:
        
        if item in MatrizB and str(item) not in MatrizC:
            MatrizC.append(str(item) + '\n')
    lista_arquivo(C, MatrizC)
```
### Tarefa 04
```python
def arquivo_lista(nomearquivo):
    lista = []
    arq = open(nomearquivo)
    
    for linha in arq:
        linha = linha.replace('\n','').lower()
        lista.append(linha)
        
    arq.close()
    
    return lista

def lista_dicionario(lista):
    dicionario = {}
    
    for frase in lista:
        for palavra in frase.split():
            for letra in palavra:
                if not letra.isalpha(): palavra = palavra.replace(letra, '')
            
            if palavra: dicionario[palavra] = dicionario.get(palavra, 0) + 1
    
    return dicionario

def contagem(arquivo):
    ListaA = arquivo_lista(arquivo)
    
    DicionarioA = lista_dicionario(ListaA)
    
    return (sum(list(DicionarioA.values())), len(ListaA))
```
### Tarefa 05
```python
def arquivo_lista(nomearquivo):
    lista = []
    arq = open(nomearquivo)
    
    linha = arq.readline()
    linha = linha.replace('\n','').upper()
    
    for i in range(0,len(linha),3):
                lista.append(linha[i:i+3])
                
    arq.close()
    
    return lista


def lista_arquivo(nomearquivo, lista):
    arq = open(nomearquivo, 'w')

    lista = '-'.join(lista)

    arq.write(lista)
        
    arq.close()


def traducao_rna(arquivo_entrada, arquivo_saida):
    DicionarioA = {'UUU':'Phe','CUU':'Leu','UUA':'Leu','AAG':'Lis','UCU':'Ser','UAU':'Tyr','CAA':'Gln'}
    
    ListaA = arquivo_lista(arquivo_entrada)
    ListaB = []
    
    for tripla in ListaA:
        ListaB.append(DicionarioA[tripla])
    
    lista_arquivo(arquivo_saida, ListaB)
```
