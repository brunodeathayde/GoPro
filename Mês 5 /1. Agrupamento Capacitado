# 🏫 Problema de Agrupamento de Capacitado (SCP) – Instância Real 

## 📌 Descrição do Problema

Este repositório apresenta uma instância real do **Problema de Agrupamento Capacitado (Capacitated Clustering Problem – CCP)** aplicada à alocação eficiente de estudantes em escolas próximas às suas residências.

O objetivo principal é determinar o agrupamento e a atribuição ótima de alunos às instituições de ensino, respeitando rigorosamente as capacidades de cada escola para cada nível de escolaridade e atendendo à demanda individual dos estudantes.

---

## 🎯 Enunciado do Problema

Desenvolver e analisar métodos de resolução (algoritmos aproximados, heurísticas ou metaheurísticas) para resolver o **Student Clustering Problem (SCP)**, otimizando a distribuição geográfica dos alunos em relação às escolas e garantindo o cumprimento de restrições operacionais e de capacidade.

---

## 🧠 Descrição do Problema

Cada aluno e cada escola representam pontos no espaço geográfico (com coordenadas de latitude e longitude). 

O planejamento deve garantir que:
- **Atendimento de Demanda:** Todos os estudantes sejam alocados a uma escola correspondente ao seu nível escolar.
- **Respeito às Capacidades:** A capacidade máxima de cada escola por nível de escolaridade não seja ultrapassada.
- **Minimização de Distância/Custo:** A distância total percorrida pelos estudantes de suas residências até as escolas atribuídas seja minimizada.

Por pertencer à classe de problemas **NP-difícil (NP-hard)**, a obtenção de soluções exatas para instâncias de médio e grande porte exige o desenvolvimento de algoritmos aproximados, heurísticas e metaheurísticas eficientes.

---

Uma instância real é apresentada nas planilhas ** Alunos.xlsx ** e ** Escolas.xlsx **. A estrutura de dados é descrita a seguir.

## 🌍 Dados da Instância

| Aluno | x | y | série |
| :---: | :---: | :---: | :---: |
| 1 | -39,1915 | -3,1224 | 1 |
| 2 | -38,142 | -4,15335 | 1 |
| 3 | -38,6469 | -4,04675 | 1 |
| 4 | -39,0504 | -3,0661 | 1 |
| 5 | -38,6846 | -3,1638 | 1 |
| 6 | -38,0232 | -4,0208 | 1 |



| | Series | | | | | | | | | | |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Escolas** | **1** | **2** | **3** | **4** | **5** | **6** | **7** | **8** | **9** | **x** | **y** |
| 1 | 16 | 15 | 23 | 17 | 22 | 24 | 17 | 14 | 24 | -38,6832 | -3,89183 |
| 2 | 18 | 18 | 17 | 16 | 21 | 23 | 12 | 16 | 23 | -38,6878 | -3,91397 |
| 3 | 20 | 13 | 24 | 20 | 19 | 21 | 21 | 15 | 22 | -38,6818 | -3,89891 |
| 4 | 15 | 17 | 24 | 14 | 20 | 19 | 23 | 18 | 24 | -38,6847 | -3,89245 |
| 5 | 12 | 10 | 10 | 21 | 25 | 18 | 21 | 12 | 19 | -38,6847 | -3,89245 |
| 6 | 25 | 12 | 11 | 14 | 24 | 23 | 21 | 19 | 19 | -38,6818 | -3,89891 |




---

## ⚙️ Métodos de Resolução

- **Programação Inteira / Exata (MILP)** – viável apenas para instâncias de pequeno porte.
- **Algoritmos de Agrupamento Heurístico (K-Means Modificado / Capacitado)** – agrupamento baseado em proximidade com controle de capacidade.
- **Metaheurísticas**:
  - **GRASP (Greedy Randomized Adaptive Search Procedure)** – construção gulosa adaptativa com busca local.
  - **Algoritmos Genéticos (AG)** – evolução de populações de atribuição.
  - **Simulated Annealing (SA)** – exploração de vizinhanças para evitar ótimos locais.
  - **Busca Tabu** – prevenção de ciclos de otimização durante a alocação.

---

## 📚 Referências

- Mulvey, J. M., & Beck, M. P. (1984). *Solving capacitated clustering problems*. Operations Research, 32(2), 439-448.
- Geetha, S., et al. (2009). *Solving Capacitated Clustering Problem using Metaheuristic Approaches*.
- Ahmadi, S., & Osborne, M. R. (2007). *The Capacitated Clustering Problem: Formulations and Algorithms*.

---

## 🚀 Possíveis Extensões

- Inclusão de **limites de distância máxima caminhavel** por aluno (zonas de corte).
- Consideração de **rotas de transporte escolar municipal** agregadas às escolas.
- Integração de **diferentes turnos escolares** (matutino, vespertino e noturno).
- Balanceamento da **diversidade socioeconômica** entre as turmas e estabelecimentos.

## 🎥 Vídeo Explicativo

[![Vídeo demonstrando a aplicação do Problema de Agrupamento Capacitado (CCP/SCP) para a alocação eficiente de estudantes em escolas próximas às suas residências.](https://img.youtube.com/vi/qBTvWm4zAT4/maxresdefault.jpg)](https://youtu.be/qBTvWm4zAT4)
