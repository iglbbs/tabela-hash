# Dicionário com Tabela Hash em C

## Atividade Avaliativa 3 - Estrutura de Dados

Este projeto foi desenvolvido como parte da atividade avaliativa da disciplina de Estrutura de Dados. O objetivo é implementar um sistema de dicionário em linguagem C utilizando uma **tabela hash** com tratamento de colisões por meio de **listas encadeadas**.

O programa permite cadastrar palavras com suas respectivas definições, buscar palavras, remover registros, visualizar a tabela hash e consultar estatísticas sobre sua utilização.

---

## Funcionalidades

O sistema possui as seguintes funcionalidades:

* Inserir palavras e definições;
* Buscar palavras cadastradas;
* Remover palavras da tabela;
* Exibir a tabela hash completa;
* Tratar colisões usando listas encadeadas;
* Exibir estatísticas da tabela hash;
* Liberar a memória alocada dinamicamente ao encerrar o programa.

---

## Estrutura dos Dados

Cada registro armazenado na tabela hash contém:

* Palavra;
* Definição;
* Ponteiro para o próximo nó da lista encadeada.

A estrutura utilizada no programa é:

```c
typedef struct No {
    char palavra[MAX_PALAVRA];
    char definicao[MAX_DEFINICAO];
    struct No *proximo;
} No;
```

A tabela hash é representada por um vetor de ponteiros:

```c
No *tabela[TAMANHO_TABELA];
```

Cada posição da tabela pode apontar para uma lista encadeada, permitindo armazenar mais de uma palavra no mesmo índice em caso de colisão.

---

## Funcionamento da Tabela Hash

A função hash utilizada calcula a soma dos valores ASCII dos caracteres da palavra e aplica o operador módulo pelo tamanho da tabela.

```c
int funcao_hash(char *palavra) {
    int soma = 0;
    int i = 0;

    while (palavra[i] != '\0') {
        soma = soma + palavra[i];
        i++;
    }

    return soma % TAMANHO_TABELA;
}
```

Com isso, cada palavra recebe um índice entre `0` e `TAMANHO_TABELA - 1`.

---

## Tratamento de Colisões

As colisões são tratadas utilizando **listas encadeadas**.

Quando duas ou mais palavras geram o mesmo índice na tabela hash, elas são armazenadas na mesma posição da tabela, formando uma lista encadeada.

A inserção de novos elementos é feita no início da lista correspondente ao índice calculado pela função hash.

Exemplo:

```text
Indice [3]: [casa] -> [mesa] -> [livro]
```

Nesse caso, as palavras `casa`, `mesa` e `livro` ficaram armazenadas no mesmo índice da tabela.

---

## Estatísticas Exibidas

O programa exibe as seguintes estatísticas:

* Tamanho da tabela;
* Total de elementos cadastrados;
* Quantidade de posições usadas;
* Quantidade de posições vazias;
* Quantidade de colisões;
* Fator de carga;
* Tamanho da maior lista encadeada.

O fator de carga é calculado da seguinte forma:

```c
fator_carga = total_elementos / TAMANHO_TABELA;
```

Esse valor indica o nível de ocupação da tabela hash.

---

## Requisitos Técnicos Atendidos

O projeto atende aos seguintes requisitos técnicos:

* Linguagem C;
* Uso de `struct`;
* Uso de ponteiros;
* Alocação dinâmica de memória com `malloc`;
* Liberação de memória com `free`;
* Implementação de listas encadeadas;
* Implementação de tabela hash;
* Tratamento de colisões;
* Menu interativo no terminal.

---

## Como Compilar

Para compilar o programa utilizando o GCC, execute:

```bash
gcc main.c -o dicionario
```

Caso o arquivo tenha outro nome, substitua `main.c` pelo nome correto do arquivo.

Exemplo:

```bash
gcc dicionario.c -o dicionario
```

---

## Como Executar

Após compilar, execute o programa com:

### Linux ou macOS

```bash
./dicionario
```

### Windows

```bash
dicionario.exe
```

---

## Menu do Sistema

Ao executar o programa, será exibido o seguinte menu:

```text
1 - Inserir palavra
2 - Buscar palavra
3 - Remover palavra
4 - Mostrar tabela
5 - Mostrar estatisticas
0 - Sair
```

O usuário deve escolher uma opção digitando o número correspondente.

---

## Exemplo de Uso

### Inserir palavra

```text
Digite a palavra: casa
Digite a definicao: Lugar onde uma pessoa mora
```

### Buscar palavra

```text
Digite a palavra a buscar: casa
```

Saída esperada:

```text
Palavra   : casa
Definicao : Lugar onde uma pessoa mora
```

### Exibir tabela

```text
Indice [ 0]: (vazio)
Indice [ 1]: [casa]
Indice [ 2]: (vazio)
...
```

---

## Organização dos Commits

O desenvolvimento pode ser dividido entre os integrantes do grupo da seguinte forma:

| Integrante   | Responsabilidade                                              |
| ------------ | ------------------------------------------------------------- |
| Igor | Estrutura inicial, constantes, `struct`, tabela e função hash |
| João | Funções de inserção e busca                                   |
| Heitor | Funções de remoção, exibição da tabela e estatísticas         |
| Gustavo | Menu principal, leitura de dados e liberação de memória       |

Cada integrante deve realizar pelo menos um commit relevante relacionado à sua parte no projeto.

---

## Integrantes

Preencha abaixo com os dados dos integrantes do grupo:

| Nome completo        | 
| -------------------- | 
| Igor de Almeida Oliveira | 
| João Guilherme Telles Ditzel | 
| Heitor Domingos de Carvalho Sauer |   
| Gustavo Henrique Witsmiszyn |    
