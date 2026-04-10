# aula_mpi
# Relatório da NOME DA ATIVIDADE

**Disciplina:** Programção concorrente distribuida 
**Aluno(s):** Stevan Gutemberg Silva Serpa
**Turma:** Analise e desenvolvimento de sistemas
**Professor:** Rafael
**Data:** 10/04/2026

---

# 1. Descrição do Problema
O programa desenvolvido tem como objetivo analisar a similaridade entre perguntas presentes em um conjunto de dados textual. O sistema lê um dataset contendo milhares de perguntas e calcula a similaridade entre todos os pares possíveis de perguntas utilizando métricas de comparação de texto.

O algoritmo percorre todas as combinações possíveis entre as perguntas do dataset e calcula uma medida de similaridade entre elas. Ao final do processamento, o programa retorna os pares de perguntas mais semelhantes encontrados no conjunto de dados.

Nos testes realizados, foi utilizado um dataset contendo aproximadamente 5000 perguntas, gerando cerca de 12.497.500 pares de comparações entre perguntas.

Devido ao grande volume de comparações necessárias, o processamento pode se tornar bastante demorado quando executado de forma sequencial. Por esse motivo, foi implementada também uma versão paralela do algoritmo utilizando múltiplos processos para dividir o trabalho entre diferentes núcleos do processador.

O objetivo da paralelização é reduzir o tempo total de execução, distribuindo as comparações entre vários processos executados simultaneamente.

Questões respondidas

Qual é o objetivo do programa?

Identificar os pares de perguntas mais semelhantes dentro de um grande conjunto de dados.

Qual o volume de dados processado?

Foram processados aproximadamente 12.497.500 pares de perguntas.

Qual algoritmo foi utilizado?

Foi utilizado um algoritmo de comparação de similaridade textual que calcula a proximidade entre duas perguntas com base em suas características textuais.

Qual a complexidade aproximada do algoritmo?

A complexidade aproximada do algoritmo é O(n²), pois cada pergunta precisa ser comparada com todas as outras perguntas do dataset.

---

# 2. Ambiente Experimental

Descreva o ambiente em que os experimentos foram realizados.

## Orientações

Os experimentos foram realizados em um computador pessoal utilizando Python e a biblioteca de paralelização MPI.
| Item                        | Descrição |
| --------------------------- | --------- |
| Processador                 |    Processador Intel/AMD       |
| Número de núcleos           |   8 núcleos (aprox.)        |
| Memória RAM                 |     8 GB      |
| Sistema Operacional         |     Windows 10      |
| Linguagem utilizada         |      Python     |
| Biblioteca de paralelização |    mpi4py       |
| Compilador / Versão         |    Python 3.13       |

---

# 3. Metodologia de Testes

Para avaliar o desempenho do algoritmo, foram realizados testes comparando a execução da versão serial com a versão paralela utilizando diferentes quantidades de processos.

O tempo de execução foi medido utilizando funções de temporização presentes no próprio código Python. Cada execução mede o tempo total necessário para processar todas as comparações entre perguntas.

Foi utilizado sempre o mesmo dataset durante todos os experimentos para garantir consistência nos resultados.

Configurações testadas

Foram executados experimentos nas seguintes configurações:

1 processo (versão serial)
2 processos
4 processos
8 processos
12 processos
Procedimento experimental

Para cada configuração foi executado o programa e registrado o tempo total de execução. Todos os testes foram realizados na mesma máquina, sem execução de outras tarefas pesadas simultaneamente, para evitar interferências nos resultados.

---

# 4. Resultados Experimentais

Preencha a tabela com os **tempos médios de execução** obtidos.

## Orientações

* O tempo deve ser informado em **segundos**
* Utilizar a **média das execuções**

| Nº Threads/Processos | Tempo de Execução (s) |
| -------------------- | --------------------- |
| 1                    |          23.28             |
| 2                    |            27.50           |
| 4                    |          17.62             |
| 8                    |           12.49            |
| 12                   |         10.95              |

---

# 5. Cálculo de Speedup e Eficiência

## Fórmulas Utilizadas

### Speedup

```
Speedup(p) = T(1) / T(p)
```

Onde:

* **T(1)** = tempo da execução serial
* **T(p)** = tempo com p threads/processos

### Eficiência

```
Eficiência(p) = Speedup(p) / p
```

Onde:

* **p** = número de threads ou processos

---

# 6. Tabela de Resultados

Preencha a tabela abaixo utilizando os tempos medidos.

| Threads/Processos | Tempo (s) | Speedup | Eficiência |
| ----------------- | --------- | ------- | ---------- |
| 1                 |     23.28      | 1.0     | 1.0        |
| 2                 |      27.50     |     0.85    |      0.42      |
| 4                 |     17.62      |   1.32      |     0.33       |
| 8                 |    12.49       |     1.86    |       0.23     |
| 12                |       10.95    |   2.12      |     0.18       |

---

# 7. Gráfico de Tempo de Execução


![Gráfico Tempo Execução](graficos/TEMPO.png)

---

# 8. Gráfico de Speedup


![Gráfico Speedup](graficos/SPEEDUP.png)

---

# 9. Gráfico de Eficiência



![Gráfico Eficiência](graficos/EFICIENCIA.png)

---

# 10. Análise dos Resultados

Observa-se que o aumento do número de processos contribuiu para a redução do tempo de execução do programa, especialmente nas configurações com maior paralelismo.

Entretanto, a execução com 2 processos apresentou tempo maior que a execução serial, o que pode ocorrer devido ao overhead de criação e comunicação entre processos.

À medida que o número de processos aumenta (4, 8 e 12), o tempo de execução diminui significativamente, demonstrando que a divisão da carga de trabalho entre múltiplos processos permite acelerar o processamento.

Apesar disso, o speedup obtido não é linear, ou seja, não cresce proporcionalmente ao número de processos. Isso ocorre devido a fatores como:

overhead de paralelização
comunicação entre processos
sincronização dos resultados
limitações de hardware
contenção de memória e cache

Também é possível observar que a eficiência diminui conforme o número de processos aumenta, o que é um comportamento esperado em aplicações paralelas.

---

# 11. Conclusão

A implementação paralela do algoritmo permitiu reduzir o tempo total de execução do processamento de similaridade entre perguntas.

O melhor desempenho foi obtido utilizando 12 processos, atingindo o menor tempo de execução entre os experimentos realizados.

Mesmo que o speedup não tenha sido perfeitamente linear, a paralelização demonstrou ser uma abordagem eficiente para lidar com problemas computacionalmente intensivos, como a comparação de milhões de pares de dados.

Como possíveis melhorias futuras, poderiam ser implementadas otimizações no algoritmo de comparação, melhor balanceamento de carga entre os processos e estratégias mais eficientes de comunicação entre processos.

---
