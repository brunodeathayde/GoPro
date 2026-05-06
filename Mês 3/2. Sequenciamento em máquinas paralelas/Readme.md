# Problema de Programação em Máquinas Paralelas com Setups – Instância Real (Rochas Ornamentais)

📌 **Descrição do Problema**

Este repositório apresenta uma instância do **Parallel Machine Scheduling Problem com tempos de setup dependentes da sequência (PMSP-SDST)** baseada em um cenário real de produção de rochas ornamentais.

O problema consiste em determinar a alocação e a ordem de processamento de diferentes produtos de granito e mármore em múltiplas máquinas paralelas, levando em conta tempos de processamento e tempos de setup que variam conforme a sequência escolhida.

---

🎯 **Enunciado do Problema**

Distribuir e sequenciar os produtos em máquinas paralelas de forma a minimizar o tempo total de produção (*makespan*) ou o atraso máximo (*Lmax*), respeitando os tempos de processamento e os setups dependentes da sequência.

---

🧠 **Descrição do Problema**

Cada produto de rocha ornamental possui:

- um tempo de processamento específico em cada máquina;
- tempos de setup que dependem da sequência de produção.

As máquinas podem operar em paralelo, mas cada uma só pode processar um produto por vez.  
Cada troca de produto em uma máquina exige um tempo de preparação adicional.

O objetivo é determinar:

- em qual máquina cada produto será processado;
- em que ordem os produtos serão processados em cada máquina;

de forma que o tempo total de produção seja minimizado.

Este problema é característico do **Parallel Machine Scheduling Problem com SDST**, amplamente aplicado em indústrias de corte e beneficiamento de rochas ornamentais.

---

📊 **Dados da Instância**

### Produtos

| Código | Produto          |
|--------|------------------|
| 1      | Branco Ceará OS  |
| 2      | Branco Alpha     |
| 3      | Juparaná Gold    |
| 4      | Branco Nevasca   |
| 5      | Branco Ceará PS  |
| 6      | Bianco Antico    |
| 7      | Grigio Monet     |
| 8      | Rain Forest      |
| 9      | Crema Riviera    |
| 10     | Preto Ceará      |

---

### Tempos de Processamento (em minutos)

| Máquina | 1  | 2  | 3  | 4  | 5  | 6  | 7  | 8  | 9  | 10 |
|---------|----|----|----|----|----|----|----|----|----|----|
| M1      | 7  | 19 | 14 | 11 | 8  | 12 | 5  | 18 | 8  | 12 |
| M2      | 9  | 9  | 20 | 5  | 8  | 20 | 18 | 16 | 14 | 16 |

---

### Matriz de Setups (em minutos)

| De/Para | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 |
|---------|---|---|---|---|---|---|---|---|---|----|
| **1**   | 0 | 9 | 15| 7 | 5 | 1 | 9 | 1 | 9 | 1  |
| **2**   | 9 | 0 | 9 |11 | 1 | 0 |13 | 1 | 3 | 4  |
| **3**   |15 | 9 | 0 | 2 | 0 | 5 |15 |13 |12 | 2  |
| **4**   | 7 |11 | 2 | 0 | 5 | 9 | 8 | 7 |14 |13  |
| **5**   | 5 | 1 | 0 | 5 | 0 | 2 |15 |11 | 4 | 9  |
| **6**   | 1 | 0 | 5 | 9 | 2 | 0 |14 | 9 | 0 | 1  |
| **7**   | 9 |13 |15 | 8 |15 |14 | 0 | 0 |15 |13  |
| **8**   | 1 | 1 |13 | 7 |11 | 9 | 0 | 0 | 8 | 6  |
| **9**   | 9 | 3 |12 |14 | 4 | 0 |15 | 8 | 0 |10  |
| **10**  | 1 | 4 | 2 |13 | 9 | 1 |13 | 6 |10 | 0  |

---

📚 **Referência**

- Estudo de caso em empresa de produção de rochas ornamentais (instância real).  
- Literatura de apoio:  
  - Lin, S.-W., & Ying, K.-C. (2022). *Single machine scheduling problems with sequence-dependent setup times and precedence delays.* Scientific Reports, 12, Article 9430.  
  - Pinedo, M. (2016). *Scheduling: Theory, Algorithms, and Systems.* Springer.  
  - Allahverdi, A., Gupta, J. N. D., & Aldowaisan, T. (1999). *A review of scheduling research involving setup considerations.* Omega, 27(2), 219–239.  

---

🚀 **Possíveis Extensões**

- Minimização explícita do atraso máximo (*Lmax*)  
- Inclusão de múltiplas máquinas heterogêneas (com capacidades diferentes)  
- Problema multiperíodo com diferentes turnos de produção  
- Integração com planejamento da produção e logística  
- Métodos de solução:  
  - Programação Inteira  
  - Algoritmos Genéticos  
  - GRASP  
  - VNS  
  - Tabu Search  

