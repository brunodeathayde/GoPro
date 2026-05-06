# Problema de Programação Job Shop – Instância Real (Acessórios Militares)

📌 **Descrição do Problema**

Este repositório apresenta uma instância do **Job Shop Scheduling Problem (JSSP)** baseada em um cenário real de produção de acessórios militares.

O problema consiste em determinar a ordem de execução das operações de diferentes jobs em múltiplas máquinas, respeitando tempos de processamento e sequências de operações, de modo a minimizar o tempo total de conclusão (*makespan*) ou atrasos.

---

🎯 **Enunciado do Problema**

Sequenciar as operações de todos os jobs em suas respectivas máquinas, respeitando a ordem tecnológica de cada produto, de forma a minimizar o tempo total de produção ou atrasos.

---

🧠 **Descrição do Problema**

Cada job representa um produto militar (ex.: colete, cinto, mochila).  
Cada job possui uma sequência de operações que devem ser realizadas em máquinas específicas.  
Cada operação tem um tempo de processamento definido.  

Restrições:
- Cada máquina só pode processar uma operação por vez.  
- A ordem das operações de cada job deve ser respeitada.  
- O objetivo é minimizar o *makespan* ou atrasos de entrega.  

Este problema é característico do **Job Shop Scheduling Problem**, amplamente aplicado em indústrias de manufatura complexa.

---

📊 **Dados da Instância**

### Jobs e Máquinas

| Job | Produto                  |
|-----|---------------------------|
| J1  | Capas de Colete           |
| J2  | Cinto de Guarnição NA     |
| J3  | Cinto Social              |
| J4  | Braçal                    |
| J5  | Coldre                    |
| J6  | Boné                      |
| J7  | Mochila                   |
| J8  | Camisas                   |
| J9  | Bornal                    |

| Máquina | Descrição                 |
|---------|---------------------------|
| M1      | Máquina de Corte          |
| M2      | Máquina de Bordado        |
| M3      | Máquina Reta              |
| M4      | Máquina Transporte-Triplo |
| M5      | Máquina Over-lock         |
| M6      | Máquina Duas-Agulhas      |
| M7      | Máquina Travete           |
| M8      | Goleira                   |
| M9      | Montagem (colagem, etc.)  |

---

### Matriz de Tempos (em minutos)

| Máquina | J1  | J2 | J3 | J4 | J5 | J6 | J7 | J8 | J9 |
|---------|-----|----|----|----|----|----|----|----|----|
| M1      | 30  | 1  | 1  | 10 | 5  | 0  | 10 | 0  | 2  |
| M2      | 35  | 0  | 0  | 20 | 0  | 15 | 0  | 15 | 0  |
| M3      | 0   | 2  | 0  | 5  | 5  | 5  | 0  | 3  | 0  |
| M4      | 10  | 0  | 0  | 3  | 3  | 0  | 0  | 0  | 2  |
| M9      | 60  | 1  | 3  | 10 | 1  | 0  | 60 | 0  | 10 |

---

### Sequência de Operações

| Job | Sequência de Máquinas |
|-----|------------------------|
| J1  | M1 → M2 → M3 → M9      |
| J2  | M1 → M9                |
| J3  | M1 → M2 → M9           |
| J4  | M1 → M2 → M3 → M9 → M4 |
| J5  | M1 → M3 → M4           |
| J6  | M2 → M3                |
| J7  | M1 → M9                |
| J8  | M2 → M3 → M9           |
| J9  | M1 → M9 → M4           |

---

📚 **Referência**

- Dados fornecidos a partir de estudo de caso em empresa de produção de acessórios militares (instância real).  
- Literatura de apoio:  
  - Pinedo, M. (2016). *Scheduling: Theory, Algorithms, and Systems.* Springer.  
  - Jain, A. S., & Meeran, S. (1999). *Deterministic job-shop scheduling: Past, present and future.* European Journal of Operational Research, 113(2), 390–434.  

---

🚀 **Possíveis Extensões**

- Minimização explícita do *makespan*  
- Inclusão de restrições de disponibilidade de máquinas  
- Problema multiperíodo com diferentes turnos de produção  
- Integração com planejamento da produção e logística  
- Métodos de solução:  
  - Programação Inteira  
  - Algoritmos Genéticos  
  - GRASP  
  - VNS  
  - Tabu Search  
