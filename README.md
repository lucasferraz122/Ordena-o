# Análise de Algoritmos de Ordenação

Este projeto foi desenvolvido em Java para implementar e comparar o desempenho de seis algoritmos de ordenação. O objetivo é analisar como eles se comportam ao processar três tipos de vetores: um com dados aleatórios, um já ordenado (melhor caso) e um ordenado de forma reversa (pior caso).

Os algoritmos que foram implementados para a comparação são:
* Comb Sort
* Gnome Sort
* Bucket Sort
* Bubble Sort (com flag de parada)
* Selection Sort
* Cocktail Sort

A análise foca em duas métricas principais:
1.  **Número de Trocas:** A contagem de quantas vezes um elemento precisou trocar de lugar.
2.  **Número de Iterações:** Uma contagem dos passos principais ou comparações que o algoritmo realizou.

## Restrições do Projeto

A maior restrição do projeto foi a **proibição estrita** de usar funções prontas de ordenação ou coleções da biblioteca Java (como `java.util.ArrayList`).

Isso foi um desafio especial para o **Bucket Sort**. Para fazê-lo funcionar, foi preciso implementar uma estrutura básica de lista ligada (LinkedList) do zero, para que ela servisse como os "baldes". Quando foi preciso ordenar os itens dentro de cada balde, usei o `Selection Sort` (e as trocas/iterações dele foram somadas ao total do Bucket Sort).

## Resultados dos Testes

Os algoritmos foram executados com os três vetores de 20 posições.

### 1. Vetor 1 (Aleatório)
`{12, 18, 9, 25, 17, 31, 22, 27, 16, 13, 19, 23, 20, 30, 14, 11, 15, 24, 26, 28}`

| Algoritmo | Trocas | Iterações |
|:---|:---|:---|
| bubble sort | 78 | 195 |
| selection sort | 18 | 209 |
| cocktail sort | 78 | 160 |
| gnome sort | 78 | 174 |
| comb sort | 22 | 138 |
| bucket sort | 7 | 155 |

### 2. Vetor 2 (Ordenado)
`{5, 7, 9, 10, 12, 14, 15, 17, 19, 21, 22, 23, 24, 25, 27, 28, 29, 30, 31, 32}`

| Algoritmo | Trocas | Iterações |
|:---|:---|:---|
| bubble sort | 0 | 20 |
| selection sort | 0 | 209 |
| cocktail sort | 0 | 20 |
| gnome sort | 0 | 19 |
| comb sort | 0 | 118 |
| bucket sort | 0 | 147 |

### 3. Vetor 3 (Reverso)
`{99, 85, 73, 60, 50, 40, 35, 30, 25, 20, 15, 14, 13, 12, 11, 10, 9, 8, 7, 6}`

| Algoritmo | Trocas | Iterações |
|:---|:---|:---|
| bubble sort | 190 | 209 |
| selection sort | 10 | 209 |
| cocktail sort | 190 | 200 |
| gnome sort | 190 | 380 |
| comb sort | 18 | 138 |
| bucket sort | 7 | 165 |

---

## Análise de Desempenho e Ranking

As tabelas de ranking abaixo mostram qual algoritmo foi melhor em cada cenário, com base nas métricas solicitadas.

### Ranking por Trocas (Menos é Melhor)

Esta tabela classifica os algoritmos pelo menor número de trocas de elementos.

| Posição | Vetor 1 (Aleatório) | Vetor 2 (Ordenado) | Vetor 3 (Reverso) |
|:---|:---|:---|:---|
| **1º** | **Bucket Sort (7)** | **Todos (0)** | **Bucket Sort (7)** |
| 2º | Selection Sort (18) | - | Selection Sort (10) |
| 3º | Comb Sort (22) | - | Comb Sort (18) |
| 4º | Bubble / Cocktail / Gnome (78) | - | Bubble / Cocktail / Gnome (190) |

**Análise (Trocas):**
O **Bucket Sort** foi o claro vencedor em economia de trocas para os vetores desordenados (Aleatório e Reverso). Sua estratégia de dividir o problema em baldes menores reduziu muito o custo de movimentação dos dados. O **Selection Sort** ficou em segundo, o que é esperado, já que sua lógica naturalmente minimiza o número de trocas.

### Ranking por Iterações (Menos é Melhor)

Esta tabela classifica os algoritmos pelo menor número de passos/comparações para ordenar.

| Posição | Vetor 1 (Aleatório) | Vetor 2 (Ordenado) | Vetor 3 (Reverso) |
|:---|:---|:---|:---|
| **1º** | **Comb Sort (138)** | **Gnome Sort (19)** | **Comb Sort (138)** |
| 2º | Bucket Sort (155) | Bubble / Cocktail (20) | Bucket Sort (165) |
| 3º | Cocktail Sort (160) | Comb Sort (118) | Cocktail Sort (200) |
| 4º | Gnome Sort (174) | Bucket Sort (147) | Bubble / Selection (209) |
| 5º | Bubble Sort (195) | Selection Sort (209) | Gnome Sort (380) |

**Análise (Iterações):**
O **Comb Sort** foi o algoritmo mais rápido (menos passos) nos cenários Aleatório e Reverso. Como ele move elementos distantes usando o "gap", ele é muito mais eficiente que os outros.

Para o **Vetor Ordenado (Melhor Caso)**, o **Gnome Sort**, **Bubble Sort** e **Cocktail Sort** foram os melhores. Isso acontece porque eles possuem mecanismos de parada (como a flag `trocou`) que os fazem perceber que o vetor já está ordenado em apenas uma passagem, parando quase imediatamente.

## Como Executar

1. Copie e cole o código postado em uma arquivo no INTELIJJ IDEA.
2. Nomeie o arquivo.java main como algoritmosdeordenacao.java.
3. Salve o código.
4. Clique no botão do Play no canto superior da tela.
