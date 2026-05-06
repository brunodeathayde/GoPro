# Problema de Programação Flow Shop – Instância Real (Indústria Têxtil)

📌 **Descrição do Problema**

Este repositório apresenta uma instância do **Flow Shop Scheduling Problem (FSSP)** baseada em um cenário real de produção da indústria têxtil.

O problema consiste em determinar a ordem de processamento de diferentes tipos de fios em uma sequência fixa de máquinas, de modo a minimizar o tempo total de produção (*makespan*) ou atrasos.

---

🎯 **Enunciado do Problema**

Sequenciar os jobs (tipos de fios) em um ambiente de flow shop, onde todos os produtos passam pelas mesmas máquinas na mesma ordem, de forma a minimizar o tempo total de produção ou atrasos.

---

🧠 **Descrição do Problema**

Cada job representa um tipo de fio produzido.  
Cada job deve passar por todas as máquinas na mesma ordem tecnológica.  
Cada operação tem um tempo de processamento específico em cada máquina.  

Restrições:
- Cada máquina só pode processar um job por vez.  
- A ordem das máquinas é fixa para todos os jobs.  
- O objetivo é minimizar o *makespan* ou atrasos de entrega.  

Este problema é característico do **Flow Shop Scheduling Problem**, amplamente aplicado em indústrias têxteis, metalúrgicas e de manufatura contínua.

---

📊 **Dados da Instância**

### Jobs (tipos de fios)

| Job | Produto   |
|-----|-----------|
| J1  | AP30/1M   |
| J2  | AP40/1T   |
| J3  | AP40/1M   |
| J4  | AP57/1    |
| J5  | LAP20/1   |
| J6  | LAP24/1   |
| J7  | LAP30/1   |
| J8  | LAP40/1   |
| J9  | LPP43/1   |
| J10 | LCY43/1   |

---

### Máquinas

| Máquina | Descrição          |
|---------|--------------------|
| M1      | Carda de algodão   |
| M2      | Carda poliéster    |
| M3      | Pré-passador       |
| M4      | Penteadeira        |
| M5      | Passador 1         |
| M6      | Passador 2         |
| M7      | Maçaroqueira       |
| M8      | Filatório          |
| M9      | Conicaleira        |

---

### Tempos de Processamento (em horas)

| Máquina | J1     | J2   | J3   | J4   | J5   | J6   | J7   | J8   | J9     | J10  |
|---------|--------|------|------|------|------|------|------|------|--------|------|
| M1      | 127.44 |10.35 |22.44 |25.08 |1.70  |0.70  |1.25  |4.19  |0.00    |4.15  |
| M2      | 0.00   |0.00  |0.00  |0.00  |0.00  |0.00  |0.00  |0.00  |229.68  |0.00  |
| M3      | 0.00   |0.00  |0.00  |0.00  |0.00  |0.00  |0.00  |0.00  |47.76   |0.00  |
| M4      | 53.12  |4.31  |9.35  |9.95  |0.72  |0.29  |0.54  |1.80  |0.00    |1.69  |
| M5      | 34.24  |2.78  |6.02  |10.36 |0.70  |0.28  |0.52  |1.72  |3.96    |1.62  |
| M6      | 36.14  |2.94  |6.36  |10.30 |0.68  |0.28  |0.52  |1.72  |3.96    |1.62  |
| M7      |111.15  |13.53 |29.34 |42.24 |1.20  |0.48  |2.10  |7.05  |9.18    |6.63  |
| M8      |95.43   |15.50 |29.90 |53.88 |0.87  |0.41  |1.10  |7.40  |15.39   |16.19 |
| M9      |112.86  |10.86 |25.47 |45.87 |1.32  |0.60  |1.29  |5.07  |14.19   |17.04 |

---

📚 **Referência**

- Silva, J. L. de C. (1996).  
  *O Problema de Sequenciamento Aplicado na Indústria Têxtil.*  
  Dissertação de Mestrado em Matemática, Universidade Federal do Ceará (UFC), Brasil.  

---

🚀 **Possíveis Extensões**

- Minimização explícita do atraso máximo (*Lmax*)  
- Inclusão de setups dependentes da sequência  
- Problema multiperíodo com diferentes turnos de produção  
- Integração com planejamento da produção e logística  
- Métodos de solução:  
  - Programação Inteira  
  - Algoritmos Genéticos  
  - GRASP  
  - VNS  
  - Tabu Search  

