# 2020a - AV4 Elementos de Sistemas - prática

| AV      | Pontos HW | Pontos SW |
| ------- | ------    | ------    |
| Teórica | 25        | 15        |
| Prática | 10        | 45        |

Avaliação 4 Elementos de Sistemas - parte prática 

- **Trabalhar sozinho**
- **150 min** total (prática + teórica)
- Ficar conectado no canal geral (para ouvir instruções)

### Começando

Você deve:

1. clonar o seu repositório (e trabalhar nele)
1. editar o arquivo `ALUNO.json`
1. não esqueça de dar `commit` e `push`

## Teórica

- https://forms.gle/6NVPniqGQaTfYQEm9

## Prática

:bulb: Antes de começar atualize o Z01-Tools:

```bash
./updateZ01tools.sh
```

:tada: **Lembre de realizar um commit (a cada questão) e dar push ao finalizar**

Questões:

1. [nasm pseudo](https://github.com/Insper/2020a-Elementos-AV4#1-0-hw-10-sw-nasm-pseudo)
1. [vm pseudo](https://github.com/Insper/2020a-Elementos-AV4#2-0-hw--10-sw-vm-pseudo)
1. [vm fatorial](https://github.com/Insper/2020a-Elementos-AV4#3-0-hw--10-sw-vm-fatorial)
1. [vm translator add3](https://github.com/Insper/2020a-Elementos-AV4#4--0-hw--5-sw-vm-translator-add3)
1. [vm translator copy](https://github.com/Insper/2020a-Elementos-AV4#5--0-hw--10-sw-vm-translator-copy)

----------------------------------

### 1. (0 HW/ 10 SW) nasm pseudo

- Arquivo: `nasm/pseudo.nasm`
- Teste: `./testeAssembly.py`

| Teste | O que testa     | pts |
|-------|-----------------|-----|
| 1     | SW(1..0) = "01" | 3   |
| 1     | SW(1..0) = "00" | 3   |
| 1     | SW(1..0) = "10" | 4   |

Transcreva para assembly do Z01 o pseudo código a seguir:

```python
 LED = 0
 if ( SW(0) == 0 ):
    if ( SW(1) == 1 ):
        LED = 3
 else
    LED = 1
```

----------------------------------

### 2. (0 HW / 10 SW) vm pseudo 

- Arquivo: `vm/pseudo/Main.vm`
- Teste: `./testeVm.py`

| Teste | O que testa              | pts |
|-------|--------------------------|-----|
| 1     | temp[2] = 1; temp[3] = 2 | 10  |

Transcreva para linguagem VM do Z01 o pseudo código a seguir:

```python
 temp[0] = 0
 while(temp[3] >= 0):     
    temp[0] = temp[0] + temp[2] + 5
    temp[3] = temp[3] - 1
```

Onde:
  - temp[0]: temporário 0
  - .....
  - temp[3]: temporário 3

----------------------------------

### 3. (0 HW / 10 SW) vm fatorial

- Arquivo: `vm/factorial/factorial.vm`
- Teste: `./testeVm.py`

| Teste | O que testa | pts |
|-------|-------------|-----|
| 1     | 0!          | 1   |
| 2     | 1!          | 2   |
| 3     | 6!          | 7   |

Escreva uma função em vm que retorna o fatorial de um 
número passado como parâmetro (argumento 0).

**Essa função pode fazer (e deve) fazer uso da função mult,
que já está implementada.**

```
0! = 1
1! = 1
6! = 6*5*4*3*2*1
```

----------------------------------

### 4. ( 0 HW / 5 SW) vm translator `add3`

- Arquivo: `vmTranslator/src/main/java/vmtranslator/Code.java`
- Teste: `./testeVm.py`

| Teste | O que testa | pts |
|-------|-------------|-----|
| 1     | add3        | 5   |

Nossa linguagem vm carece de um comando `add3` que adiciona
três elementos no topo da pilha (e não 2 como o `add` faz).

```
       add3 
  2           10
  3              <--sp
  5             
   <-- sp      
```

- Nesse exemplo os elementos no topo da pilha são o `5 3 2` após 
a execução do comando `add3` que soma os três elementos, o resultado
é guardado no lugar do 2.

A tradução do comando comando `copy` de `.vm` para `nasm` deve ser feito
no `Code.java` na linha:

``` java
} else if (command.equals("add3")) {

}
```

> exemplo: commands.add("leaw $SP, %A");

----------------------------------

### 5. ( 0 HW / 10 SW) vm translator `copy`

- Arquivo: `vmTranslator/src/main/java/vmtranslator/Code.java`
- Teste: `./testeVm.py`

| Teste | O que testa | pts |
|-------|-------------|-----|
| 1     | copy        | 10  |

Nossa linguagem vm carece de um comando `copy` que duplica
o elemento que está no topo da pilha, como demonstrado no 
exemplo a seguir:

```
       copy 
  3            3
  5            5 
   <-- sp      5
                  <--sp
```

- Nesse exemplo o elemento no topo da pilha é o `5` e após 
a execução do comando `copy` ele é duplicado e colocado na
pilha.

A tradução do comando comando `copy` de `.vm` para `nasm` deve ser feito
no `Code.java` na linha:

``` java
// LINHA 46
if (command.equals("copy")) {

}
```

> exemplo: commands.add("leaw $SP, %A");


