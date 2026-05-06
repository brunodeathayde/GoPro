# Problema de Programação em Máquina Única – Instância Real (Lin & Ying, 2022)

📌 **Descrição do Problema**

Este repositório apresenta uma instância do **Problema de Programação em Máquina Única com Setups Dependentes da Sequência (Single Machine Scheduling Problem – SDST)** baseada em uma aplicação real descrita na literatura.

O problema consiste em determinar a ordem de execução de tarefas em uma única máquina, levando em conta tempos de processamento, prazos de entrega e tempos de preparação (setups) que variam conforme a sequência escolhida.

---

🎯 **Enunciado do Problema**

Sequenciar um conjunto de tarefas em uma única máquina de forma a minimizar o atraso máximo (*Lmax*) ou o tempo total de conclusão (*makespan*), respeitando os tempos de processamento e os setups dependentes da sequência.

---

🧠 **Descrição do Problema**

O problema consiste em decidir a ordem de execução de tarefas em uma máquina única.

Cada tarefa possui:

- um tempo de processamento específico;
- um prazo de entrega;
- e um tempo de setup que depende da tarefa anterior.

A máquina só pode processar uma tarefa por vez, e cada troca de tarefa exige um tempo de preparação adicional.

O objetivo é escolher a sequência de tarefas que:

- minimize o atraso máximo ou o tempo total de conclusão;
- respeite os tempos de processamento e setups;
- e atenda às restrições de precedência, quando aplicáveis.

Este problema é característico do **Single Machine Scheduling Problem**, sendo amplamente utilizado em contextos industriais como montagem eletrônica, usinagem e logística.

---

📊 **Dados da Instância**

### Tarefas

| Job | Tempo de Processamento (p) | Prazo (d) |
|-----|-----------------------------|-----------|
| J1  | 25 min                      | 60 min    |
| J2  | 40 min                      | 120 min   |
| J3  | 35 min                      | 150 min   |
| J4  | 20 min                      | 90 min    |
| J5  | 30 min                      | 110 min   |

### Matriz de Setups (em minutos)

| De/Para | J1 | J2 | J3 | J4 | J5 |
|---------|----|----|----|----|----|
| **J1**  | 0  | 5  | 7  | 4  | 6  |
| **J2**  | 6  | 0  | 5  | 8  | 7  |
| **J3**  | 4  | 6  | 0  | 5  | 9  |
| **J4**  | 7  | 5  | 6  | 0  | 4  |
| **J5**  | 5  | 7  | 8  | 6  | 0  |

---

📚 **Referência**

- Lin, S.-W., & Ying, K.-C. (2022).  
  *Single machine scheduling problems with sequence-dependent setup times and precedence delays.*  
  Scientific Reports, 12, Article 9430.

---

🚀 **Possíveis Extensões**

- Minimização explícita do atraso máximo (*Lmax*)  
- Inclusão de restrições de precedência entre tarefas  
- Problema multiperíodo com disponibilidade limitada da máquina  
- Integração com planejamento da produção  
- Métodos de solução:  
  - Programação Inteira  
  - Regras de despacho (EDD, SPT)  
  - GRASP  
  - Algoritmos Genéticos  
  - VNS  
