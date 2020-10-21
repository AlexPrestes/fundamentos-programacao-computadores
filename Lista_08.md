# Algoritmos da Lista 08
## Caso alguém tenha os enunciados, me mande
---
### Tarefa 01
```python
def caixa_eletronico(valor):
    valor = int(valor)
    total_cedulas = {100:0,50:0,20:0,10:0,5:0,2:0}
    
    if valor%2:
        total_cedulas[5] += 1
        valor -= 5
    else:
        del total_cedulas[5]

    for notas in [100,50,20,10,2]:
        while valor >= notas:
            total_cedulas[notas] += 1
            valor -= notas
        if not total_cedulas[notas]: del total_cedulas[notas]
        
    return total_cedulas
```
### Tarefa 02
```python
def matriz_2x2_inversa(M):

    m = 2
    #matriz = []
    matriz_inv = []
    matriz_id = []
    matriz_d = []
    
    #for k in range(m):
    #    matriz.append([float(i) for i in input().split()])
    matriz = M
    
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
        
        #len_matriz = len(matriz_inv) - 1
        #for i in matriz_inv:
        #    if len_matriz:
        #        print(' '.join([format(j, '.2f') for j in i]))
        #    else:
        #        return ' '.join([format(j, '.2f') for j in i])
        #    len_matriz -= 1
        
        return matriz_inv
    else:
        return
```
### Tarefa 03
```python
def print_dict_rec(D, level=0):
    tabs = '\t'*level
    for chave in list(D.keys()):
        if not isinstance(D[chave],dict):
            print('%s%s: %s' % (tabs, chave, str(D[chave])))
        else:
            print('%s%s: {' % (tabs, chave))
            print_dict_rec(D[chave],level+1)
            print('%s}' % tabs)
```
### Tarefa 04
```python
def g(N):
    soma = 0
    for i in str(N):
        soma += int(i)
    if len(str(soma)) == 1:
        return soma
    else:
        return g(soma)
```
### Tarefa 05
```python
def Seguro(tabuleiro, N, linha, coluna):
    
    #Verifica se ocorre ataque na linha
    for i in range(N):
        if tabuleiro[linha][i]:
            return False
    
    #Verifica se ocorre ataque na coluna
    for i in range(N):
        if tabuleiro[i][coluna]:
            return False

    #Verifica se ocorre ataque na diagonal principal acima e abaixo
    for i,j in zip(range(linha,-1,-1),range(coluna,-1,-1)):
        if tabuleiro[i][j]:
            return False
    for i,j in zip(range(linha, N, 1),range(coluna, N, 1)):
        if tabuleiro[i][j]:
            return False

    #Verifica se ocorre ataque na diagonal secundária acima e abaixo
    for i,j in zip(range(linha,-1,-1),range(coluna, N, 1)):
        if tabuleiro[i][j]:
            return False
    for i,j in zip(range(linha, N, 1),range(coluna,-1,-1)):
        if tabuleiro[i][j]:
            return False
    #Se chegou aqui, então está seguro (retorna true)
    return True


def Executar(tabuleiro, N, coluna, solucao = 0):
  
    if coluna == N:
        solucao += 1
        return solucao
    
    for i in range(N):
        #Verifica se é seguro colocar a rainha naquela coluna
        if Seguro(tabuleiro, N, i, coluna):
            #Insere a rainha (marca com 1)
            tabuleiro[i][coluna] = 1
            #Chamada recursiva
            solucao = Executar(tabuleiro, N, coluna + 1, solucao)
            #Remove a rainha (backtracking)
            tabuleiro[i][coluna] = 0
    return solucao


def tabuleiro_rainhas(N):
    
    #Gerando tabuleiro
    tabuleiro = []
    
    for i in range(N):
        tabuleiro.append([0]*N)
    
    return Executar(tabuleiro, N, 0)


n = int(input())

print(tabuleiro_rainhas(n))
```
### Tarefa 06
```python
def soma_lista_rec(L):
    soma = 0
    for item in L:
        if not isinstance(item, list):
            soma += item
        else:
            soma += soma_lista_rec(item)
    return soma
```
### Tarefa 07
```python
def quantidade(l, c, M, pixels_nao_verificados=[], pixels_verificados=[]):
    for i in range(-1,2):
        for j in range(-1,2):
            if (l+i) in range(len(M)) and (c+j) in range(len(M[l+i])):
                if  M[l][c] == M[l+i][c+j] and \
                    [l+i,c+j] not in pixels_nao_verificados and \
                    [l+i,c+j] not in pixels_verificados:
                    
                    pixels_nao_verificados.append([l+i,c+j])
                    
    pixels_nao_verificados.remove([l,c])
    pixels_verificados.append([l,c])

    if len(pixels_nao_verificados):
        quantidade(pixels_nao_verificados[0][0],pixels_nao_verificados[0][1],M,pixels_nao_verificados,pixels_verificados)
        
    return len(pixels_verificados)
```
